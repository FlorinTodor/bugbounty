---
tags: [vulnerabilidad]
clase: Mass Assignment
estado: 🔴 pendiente
owasp: API3:2023 (Broken Object Property Level Authorization)
paga_bien: ⭐⭐ (alto en APIs, y poca gente lo prueba a fondo)
---
# Mass assignment

> Le mandas al servidor **más campos de los que el formulario te deja tocar**, y el backend los
> acepta sin filtrar. Vive a caballo entre [[Broken Access Control e IDOR]] (autorización) y
> [[Fallos de lógica de negocio]], pero merece nota propia porque en **APIs REST/GraphQL** es de lo
> más rentable y casi nadie lo prueba con método. Es tu especialización de APIs: míralo bien.

## Qué es (en una frase, con mis palabras)
El servidor mapea el JSON de entrada directamente al objeto/modelo (`user.update(request.body)`) sin
una allowlist de qué campos puede tocar el usuario, así que **añadiendo campos** al cuerpo modificas
propiedades que no deberías: `role`, `isAdmin`, `verified`, `balance`, `price`, `userId`, `tenantId`.

## Por qué existe (causa raíz)
Frameworks que hacen binding automático del body al modelo por comodidad:
- Rails `params.permit` mal usado / `update_attributes(params)` sin strong params.
- Node/Mongoose `Model.create(req.body)`, `Object.assign(user, req.body)`, spread `{...req.body}`.
- Spring `@ModelAttribute` sin `@JsonIgnore` / DTO.
- Django `**request.data` en un `serializer` sin `fields` restringido.
- Laravel `$model->fill($request->all())` sin `$fillable`.
El desarrollador confía en que "el formulario solo envía nombre y email", pero el endpoint acepta
cualquier clave.

## Cómo se ve en una app real (señales observables)
- Un PATCH/PUT de "editar perfil" que devuelve el objeto completo con campos que tú no enviaste
  (`"role":"user"`, `"credits":0`, `"emailVerified":false`). Esos campos que **te muestra** son
  justo los candidatos a **enviarle de vuelta**.
- Registro (`/signup`) o creación de recurso donde el response trae más de lo que el form pedía.
- APIs con documentación/OpenAPI (Swagger) donde el modelo lista campos que la UI no expone.
- GraphQL: un `input` type con más campos de los que el formulario usa (mira la introspección).

## Cómo lo pruebo (mi procedimiento)
1. Haz la acción legítima (editar perfil, crear pedido) y **captura el response completo** en Burp.
   Apunta TODOS los campos que devuelve el objeto, no solo los que enviaste.
2. En el Repeater, **añade al body** los campos sospechosos, uno o varios:
   `"role":"admin"`, `"isAdmin":true`, `"is_staff":true`, `"verified":true`, `"emailVerified":true`,
   `"accountBalance":999999`, `"price":0`, `"discount":100`, `"userId":<id de otra cuenta>`,
   `"id":<otro>`, `"tenantId":<otro>`, `"approved":true`, `"premium":true`.
3. Reenvía y **comprueba el efecto**: vuelve a leer tu perfil / recurso. ¿Se aplicó el campo?
4. Si no sabes los nombres exactos: sácalos del **response**, del **JS del front**, de la
   **documentación de la API**, de la **introspección GraphQL**, o **fuzzea** claves comunes.
5. Combínalo con [[Broken Access Control e IDOR]]: si además del campo cuela un `userId` ajeno,
   modificas el recurso de otro → account takeover o manipulación cruzada.

## Payloads / técnicas
> Fuente real: PayloadsAllTheThings (Mass Assignment) + la doc de la API concreta. No de memoria.
- Campos de privilegio: `role`, `roles`, `isAdmin`, `admin`, `is_staff`, `is_superuser`, `group`, `permissions`.
- Campos de estado: `verified`, `emailVerified`, `active`, `enabled`, `approved`, `confirmed`, `status`.
- Campos de dinero/negocio: `balance`, `credits`, `price`, `amount`, `discount`, `total`, `premium`, `plan`.
- Campos de identidad: `id`, `userId`, `user_id`, `owner`, `tenantId`, `organizationId`.
- Anidado: si el modelo tiene relaciones, prueba objetos anidados `{"user":{"role":"admin"}}`.
- Variantes de formato: prueba `snake_case` y `camelCase` de cada uno; el binding suele aceptar uno.

## Bypass de defensas (WAF, filtros)
- Si filtran por Content-Type, prueba el mismo campo como **form-urlencoded** en vez de JSON, o al revés.
- Si hay allowlist en un endpoint (`/profile`) prueba **otro endpoint** que toque el mismo modelo
  (`/admin/profile`, `/api/v1/users/{id}`, el de registro, un import/bulk).
- Duplicar la clave (`role=user&role=admin`) por si el parser se queda con la última.
- Endpoints de **creación** suelen filtrar menos que los de edición (o al revés): prueba ambos.

## Cómo lo confirmo y demuestro impacto
- **Escalada de privilegios**: pasar de user a admin = **Critical**. Demuestra accediendo a una
  función de admin después.
- **Fraude**: poner `price:0` o `balance` alto y completar una compra = **High/Critical** según app.
- **Bypass de verificación**: `emailVerified:true` saltándote el flujo = **Medium/High**.
- En el report: muestra la petición con el campo extra + la lectura posterior que prueba que se
  aplicó. Sé explícito en el impacto de negocio.

## Labs de PortSwigger
- [ ] *API testing* → **Exploiting mass assignment vulnerabilities** (está en el módulo de API testing)
- [ ] Encadénalo con los de *Access control* y los de *GraphQL* (nodos/inputs con campos de más)

## Casos reales / writeups que estudié
- BBLabs tiene labs de mass assignment sacados de reports reales → ver [[BBLabs - labs de reports reales]].
- Busca en HackerOne disclosed: "mass assignment", "hidden parameter", "privilege escalation via parameter".
- 

## Mis notas de caza (lo que aprendí en target real)
- 

Enlaces: [[MOC - Vulnerabilidades]] · [[Broken Access Control e IDOR]] · [[Fallos de lógica de negocio]] · [[APIs REST y GraphQL]] · [[Checklist maestro]]

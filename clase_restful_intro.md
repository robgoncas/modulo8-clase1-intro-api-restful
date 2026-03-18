# 🌐 Clase 1: Fundamentos de APIs RESTful

## 🧠 ¿Qué es REST?

REST (Representational State Transfer) es un estilo arquitectónico propuesto por Roy Fielding en el año 2000.

No es una tecnología ni un framework, sino un conjunto de principios para diseñar APIs escalables, simples y desacopladas.

---

## 🔗 ¿Qué es una API?

Una API es un intermediario que permite que dos sistemas se comuniquen.

Ejemplo:
- Cliente (frontend) → hace una petición
- Servidor (Node.js + Express) → responde con datos

---

## 🧩 Conceptos clave

### 🔹 Recurso
Entidad del sistema:
- usuarios
- productos
- pedidos

### 🔹 Representación
Los recursos se envían en formato JSON:

```json
{
  "id": 1,
  "nombre": "Roberto"
}
```

### 🔹 Stateless
Cada request contiene toda la información necesaria.

---

## ⚙️ Restricciones de REST

### 1. Cliente - Servidor
Separación entre frontend y backend.

### 2. Stateless
El servidor no guarda estado entre requests.
cada request debe incluir todo lo necesario para ser resuelta

### 3. Cacheable
Las respuestas pueden almacenarse.
Puede utilizar el cache del navegador para guardar informacion de tokens y respuestas del servidor.

### 4. Interfaz uniforme
Uso estándar de URLs, métodos HTTP y JSON.

---

## 🔥 REST vs Express (lo que ya sabes)

### ❌ No REST

```js
app.get('/obtenerUsuarios', (req, res) => {
  res.json(usuarios);
});
```

### ✅ REST

```js
//obtener usuarios
app.get('/usuarios', (req, res) => {
  res.json(usuarios);
});
//crear usuario
app.post('/usuarios', (req, res) => {
  res.json(usuarios);
});

//eliminar usuario
app.delete('/usuarios', (req, res) => {
  res.json(usuarios);
});

//actualizar completo usuario
app.put('/usuarios', (req, res) => {
  res.json(usuarios);
});

//actualizar parcialmente usuario
app.patch('/usuarios', (req, res) => {
  res.json(usuarios);
});
```

---

## 🔁 CRUD con Express

```js
app.get('/usuarios', (req, res) => {
  res.json(usuarios);
});

app.get('/usuarios/:id', (req, res) => {
  res.json({ id: req.params.id });
});

app.post('/usuarios', (req, res) => {
  res.status(201).json(req.body);
});

app.put('/usuarios/:id', (req, res) => {
  res.json({ actualizado: true });
});

app.delete('/usuarios/:id', (req, res) => {
  res.json({ eliminado: true });
});
```

---

## 📊 Comparación

| Concepto | No REST | REST |
|----------|--------|------|
| URL | /crearUsuario | /usuarios |
| Acción | En la URL | En HTTP |
| Estructura | Libre | Estándar |

---

## 🧠 Analogía con SQL

| Operación | REST |
|----------|------|
| SELECT | GET |
| INSERT | POST |
| UPDATE | PUT |
| DELETE | DELETE |

---

## 🧪 Actividad

Transformar estas rutas a REST:

```js
/obtenerProductos
app.get('/productos', (req, res) => {
  res.json(productos);
});

/agregarProducto
app.post('/productos', (req, res) => {
  res.status(201).json(producto);
});

/eliminarProducto
app.delete('/productos/:id', (req, res) => {
  //El código de estado HTTP 204 No Content (Sin Contenido) indica que el servidor procesó la solicitud con éxito, pero no necesita devolver ningún cuerpo de respuesta. Se usa frecuentemente para confirmar acciones (como DELETE o PUT) 
  //se envia el status http 204 y su contenido (message, code)
  res.status(204).send();
});
```

---

## 🚀 Conclusión

REST es una forma de diseñar APIs:
- Basada en HTTP
- Orientada a recursos
- Stateless
- Estándar en la industria

#  Formulario Avanzado

Contiene la evidencia sobre el formulario avanzado
el cual se desarrolla en html usando script y css para los estilos.


---

##  `index.html`

### Encabezado del documento `<head>`
- `<!DOCTYPE html>`: Define que el documento es HTML5.
- `<html lang="en">`: Establece el idioma en inglés.
- `<meta charset="UTF-8">`: Usa la codificación UTF-8.
- `<meta name="viewport"...>`: Hace el diseño adaptable a dispositivos móviles.
- `<title>Formulario Avanzado</title>`: Título en la pestaña del navegador.
- `<link rel="stylesheet"...>`: Vincula la hoja de estilos CSS.

### Estructura del formulario `<body>`
- `<div class="container">`: Contenedor principal con estilo visual.
- `<h1>`: Título del formulario.

### Barra de progreso
- `.progreso-formulario`: Barra base gris.
- `.barra-progreso`: Se llena según validaciones correctas.
- `#PorcentajeProgres`: Muestra el porcentaje en texto.

### Campos del formulario
Cada campo usa una estructura como esta:
```html
<div class="form-group">
  <label for="campo">Etiqueta</label>
  <input ... />
  <div class="mensaje-error"></div>
</div>
```
Los campos incluidos son:
- `nombre`, `apellido`: Validan mínimo dos nombres o apellidos.
- `correo`, `confirmarCorreo`: Validan formato y coincidencia.
- `contraseña`, `confirmarContraseña`: Validan patrón y fortaleza.
- `telefono`: Formato 300-123-4567.
- `fechaNacimiento`: Calcula edad automáticamente.
- `comentarios`: Área con contador de caracteres.
- `términos`: Checkbox obligatorio.

### Botón de envío
- `<button type="submit">`: Envía el formulario si todo es válido.

### Mensaje de éxito
- `<div id="mensajeExito">`: Aparece cuando se valida todo correctamente.

## Scripts
Contiene todas las validaciones:
- Validación de cada campo con `regex`.
- Cálculo de edad.
- Barra de progreso actualizable.
- Evaluación de la fortaleza de la contraseña.
- Prevención de copia/pegado en campos sensibles.
- Eventos para validar al escribir y enviar.


###  Estructura principal

```javascript
document.addEventListener("DOMContentLoaded", () => {
```
- Espera a que todo el HTML esté cargado antes de ejecutar el código.

### 🔧 Variables iniciales
```javascript
const form = document.getElementById("formularioAvanzado");
const inputs = form.querySelectorAll("input, textarea");
...
```
- Se obtienen referencias a los elementos del formulario: campos, barra de progreso, etc.

### Diccionarios de errores y éxitos
```javascript
const errores = { ... }
const exitos = { ... }
```
- Guarda los mensajes de error y éxito asociados a cada campo.

###  Funciones auxiliares
**`mostrarError(input, mensaje)`**: Muestra un mensaje rojo y marca el campo como inválido.  
**`ocultarError(input)`**: Oculta el mensaje de error.  
**`mostrarExito(input)`**: Muestra mensaje verde y marca el campo como válido.  
**`ocultarExito(input)`**: Oculta el mensaje de éxito.  

---

## Funciones de validación

### Nombre y Apellido
```javascript
function validarNombre(input)
function validarApellido(input)
```
- Validan que el usuario escriba al menos dos palabras y solo letras.

### Correo
```javascript
function validarCorreo()
function validarConfirmarCorreo()
```
- Verifican formato correcto y que ambos correos coincidan.

### Contraseña y confirmación
```javascript
function validarContraseña()
function validarConfirmarContraseña()
```
- Verifica que cumpla con el patrón (mínimo 8 caracteres, letra y número).
- Confirma coincidencia entre las dos contraseñas.

### Fortaleza de contraseña
```javascript
function Fortalezapassword(password)
function actualizarBarra(fortaleza)
```
- Evalúa la fortaleza de la contraseña y actualiza la barra visual.

### Teléfono
```javascript
function validarTelefono()
```
- Valida el formato `300-123-4567` usando una expresión regular.

### Fecha de nacimiento y edad
```javascript
function validarFecha()
function calcularEdad()
```
- Se calcula la edad a partir de la fecha.
- Se muestra automáticamente debajo del campo de fecha.

### Comentarios
```javascript
comentarios.addEventListener("input", ...)
```
- Cuenta y muestra los caracteres ingresados en tiempo real.

### Términos
```javascript
function validarTerminos()
```
- Verifica que el checkbox esté marcado.

---

##  Barra de progreso

```javascript
function actualizarProgreso()
```
- Cuenta cuántos campos han sido validados correctamente.
- Calcula un porcentaje y actualiza:
  - Texto (`0%`, `100%`)
  - Color (rojo <40%, amarillo <70%, verde ≥70%)
  - Ancho de la barra `.barra-progreso`.

---

## Eventos y envío

### Entrada en campos
```javascript
inputs.forEach((input) => {
  input.addEventListener("input", () => { ... });
});
```
- Cada vez que el usuario escribe algo, se valida ese campo y se actualiza la barra.

### Envío del formulario
```javascript
form.addEventListener("submit", function (e) { ... });
```
- Se cancela el envío con `e.preventDefault()`.
- Si todos los campos son válidos, se muestra el mensaje de éxito.
- Si algo falla, el mensaje no se muestra.

---




---

## `style.css`

### General
- `body`: Estilo del fondo, tamaño de fuente y color de fondo.
- `.container`: Caja del formulario con fondo claro, sombra y bordes.

### Estética del formulario
- `.form-group`: Espaciado entre campos.
- `label`: Estilo para etiquetas.
- `input`, `textarea`: Campos redondeados, responsivos.

### Estados de validación
- `.valido`: Borde verde.
- `.invalido`: Borde rojo.

### Barra de progreso
- `.progreso-formulario`: Contenedor gris.
- `.barra-progreso`: Relleno que aumenta con el porcentaje.

### Fortaleza de la contraseña
- `.password-strength`: Barra base.
- `.strength-level`: Nivel de fortaleza.
- `.strength-text`: Texto que describe la fuerza.

### Botón
- `.btn-enviar`: Color verde, escala al pasar el mouse.
- `button:disabled`: Color gris cuando está deshabilitado.

### Mensajes
- `.mensaje-error`: Rojo, animado.
- `.mensaje-exito`: Verde, animado.

### Comentarios
- `.contador-caracteres`: Muestra cuántos caracteres van.

---


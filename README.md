# 🛒 Sistema CRUD de Productos - Django

Este proyecto es una aplicación web desarrollada con Django que implementa un sistema CRUD (Create, Read, Update, Delete) para la gestión de productos.

Fue desarrollado como parte de la materia Plataformas de Programación Empresarial.

#Integrantes:
-Juan José Álvarez Restrepo 
-Juan Sebastián Jaramillo
-Maria Alexandra Jiménez Suárez

---

## 📌 Descripción del sistema

La aplicación permite administrar productos con los siguientes datos:
- Nombre
- Descripción
- Precio
- Stock
- Fecha de creación

Permite:
- Crear productos
- Listarlos
- Editarlos
- Eliminarlos

---

## 🏗️ Arquitectura

El proyecto sigue el patrón MVT de Django:

CRUD-main/
 core/
 productos/
  models.py
  views.py
  forms.py
  urls.py
  templates/
 db.sqlite3
 manage.py

---

## 🧠 Modelo (models.py)

Define la estructura de la base de datos.

- CharField: texto corto (nombre)
- TextField: texto largo (descripción)
- DecimalField: números con decimales (precio)
- IntegerField: números enteros (stock)
- DateTimeField: fecha automática

Meta:
- Ordena por fecha descendente
- Define nombres en admin

__str__:
- Devuelve nombre y precio del producto

---

## 🧾 Formularios (forms.py)

Usa ModelForm:
- Genera formularios automáticamente
- Valida datos
- Usa widgets para mejorar interfaz

Métodos importantes:
- is_valid(): valida datos
- save(): guarda en base de datos

---

## ⚙️ Vistas (views.py)

### producto_lista
- Usa Producto.objects.all()
- Retorna todos los productos
- Renderiza template lista.html

### producto_crear
Flujo:
1. Detecta POST
2. Crea formulario con request.POST
3. Valida con is_valid()
4. Guarda con save()
5. Mensaje con messages.success
6. Redirección con redirect

### producto_editar
Flujo:
1. Busca producto con get_object_or_404
2. Si POST:
   - Usa instance=producto
   - Valida y guarda
3. Si GET:
   - Muestra datos actuales

### producto_eliminar
Flujo:
1. Busca producto
2. Espera confirmación POST
3. Ejecuta delete()
4. Redirige

---

## 🔗 URLs

- / → lista
- /crear/ → crear
- /editar/id → editar
- /eliminar/id → eliminar

---

## 🔄 Flujo del sistema

Usuario → request → view → modelo → base de datos → respuesta HTML

---

## 🚀 Mejoras

- Login
- API REST
- Búsqueda
- Paginación

---

Proyecto académico - Plataformas de Programación Empresarial

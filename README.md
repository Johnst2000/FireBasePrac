# FireBasePrac - Sistema de Monitoreo de Sensores en Tiempo Real

Este proyecto es una aplicación móvil desarrollada para la plataforma Android como parte del plan de estudios de la materia de Aplicaciones Móviles. Su propósito fundamental es demostrar la integración de aplicaciones móviles con servicios de bases de datos en la nube mediante el uso de Firebase Realtime Database.

## Descripcion General

La aplicación permite la visualización y gestión remota de cuatro variables críticas de sensores: Temperatura, Humedad, Velocidad y Presión. Implementa una arquitectura cliente-servidor donde Android actúa como el cliente que consume y modifica datos almacenados en un nodo JSON centralizado en Firebase.

## Caracteristicas Funcionales

### 1. Monitoreo en Tiempo Real
La sección superior de la interfaz está dedicada a la lectura de datos. Utiliza escuchas de eventos (EventListeners) que detectan cualquier cambio en la base de datos y actualizan la interfaz de usuario de forma inmediata sin necesidad de refrescar la pantalla manualmente.

### 2. Seteo y Control de Sensores
La sección inferior permite la interacción activa. A través de campos de entrada (EditText), el usuario puede definir nuevos valores para cada sensor. Al presionar el botón "Set", la aplicación realiza una operación de escritura asíncrona hacia Firebase, actualizando el estado global para todos los clientes conectados.

## Diseño Visual y Codificacion de Colores

Para mejorar la experiencia del usuario y la interpretabilidad de los datos, se ha implementado un sistema de identificación visual basado en colores para cada categoría:

- Temperatura: Color Rojo (#F44336). Asociado al calor y alertas térmicas.
- Humedad: Color Azul (#2196F3). Representa el elemento agua y niveles de humedad relativa.
- Velocidad: Color Naranja (#FF9800). Indica movimiento y dinamismo.
- Presion: Color Verde (#4CAF50). Representa niveles de estabilidad atmosférica.

## Especificaciones Tecnicas

- Lenguaje de Programacion: Java (JDK 11+).
- Entorno de Desarrollo: Android Studio.
- Version de Android: Compatible con niveles de API recientes (Android 10+).
- Backend: Firebase Realtime Database (Estructura NoSQL).
- Componentes de UI: LinearLayout, ScrollView, ImageView, Button, TextView y EditText.

## Arquitectura del Proyecto

- MainActivity.java: Contiene la lógica principal, la inicialización de referencias a la base de datos y la implementación de los ValueEventListeners.
- activity_main.xml: Define la estructura jerárquica de la interfaz, utilizando ScrollView para garantizar la navegabilidad en diferentes tamaños de pantalla.
- Firebase Database: Actúa como el motor de sincronización entre dispositivos.

## Guia de Configuracion de Firebase

1. Registro del Proyecto: Registrar el nombre de paquete "com.example.firebaseprac" en la consola de Firebase.
2. Archivo de Configuracion: Incorporar el archivo google-services.json en el directorio /app del proyecto.
3. Reglas de Seguridad: Configurar las reglas de Realtime Database para permitir operaciones de lectura y escritura durante la fase de desarrollo:
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
4. Estructura de Datos Requerida:
   sensores/
     ├── humedad
     ├── presion
     ├── temperatura
     └── velocidad

## Detalles de Implementacion

La aplicación utiliza el método addValueEventListener para cada referencia de sensor. Esto permite recibir un DataSnapshot cada vez que un valor cambia en la nube. La conversión de datos se maneja de forma segura mediante el parseo de strings a flotantes antes de ser enviados al servidor para evitar errores de tipo de dato en la base de datos NoSQL.

---
Materia: Aplicaciones Moviles
Semestre: 6to Semestre
Institucion: Facultad de Ingenieria

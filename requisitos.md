# Requisitos Funcionales y No Funcionales — ATS Mini (AI-Powered)

Este documento detalla los Requisitos Funcionales (RF) y Requisitos No Funcionales (RNF) de la plataforma inteligente de análisis y gestión de postulaciones laborales (**ATS Mini**). El sistema está diseñado bajo una arquitectura de API RESTful con control de acceso basado en roles para **Postulantes**, **Reclutadores** y **Administradores**.

---

## 🔐 Módulo de Autenticación y Cuentas de Usuario

* **RF01 — Registro de Cuentas**: El sistema debe permitir el registro de nuevos usuarios en la plataforma.
* **RF02 — Credenciales de Acceso**: El sistema debe permitir a los usuarios iniciar sesión utilizando sus credenciales (email y contraseña).
* **RF03 — Generación de Token**: El sistema debe generar y retornar un token de acceso seguro e inmutable (JWT) válido tras un inicio de sesión exitoso.
* **RF04 — Seguridad Basada en Roles**: El sistema debe restringir el acceso a los recursos y endpoints basándose en los roles del sistema: `ROLE_POSTULANTE`, `ROLE_RECLUTADOR`, `ROLE_ADMIN`.
* **RF05 — Estado de las Cuentas**: El sistema debe gestionar el ciclo de vida y estado de las cuentas de usuario (ACTIVA, BLOQUEADA, INACTIVA).

---

## 👤 Módulo de Usuarios (Gestión de Identidades)

* **RF06 — ABM de Usuarios**: El sistema debe permitir al administrador realizar el ABM (Alta, Baja, Modificación) de los perfiles de usuario.
* **RF07 — Correo Único**: El sistema debe garantizar que el correo electrónico (`email`) sea único e irrepetible para cada usuario registrado.
* **RF08 — Listado General**: El sistema debe permitir listar el total de usuarios registrados con fines de auditoría y administración.
* **RF09 — Consulta por Identificador**: El sistema debe permitir la consulta detallada de los datos personales y de contacto de un usuario por medio de su ID único.
* **RF10 — Registro de Habilidades del Postulante**: El sistema debe permitir al postulante asociar una o más habilidades técnicas (`Skills`) del catálogo a su perfil personal.
* **RF11 — Categorización de Seniority**: El sistema debe permitir al postulante registrar y actualizar su nivel de experiencia profesional mediante la escala de seniority: `JUNIOR`, `SEMISENIOR`, `SENIOR`.
* **RF12 — Enlace de Portafolio**: El sistema debe permitir al postulante registrar y actualizar el enlace a su portafolio digital externo (`link_portfolio`).
* **RF13 — Auditoría de Creación**: El sistema debe registrar de forma automática y no modificable la fecha y hora exacta (`fecha_creacion`) en la que se registra un usuario en el sistema.

---

## 💼 Módulo de Ofertas Laborales (Oferta de Empleo)

* **RF14 — ABM de Ofertas**: El sistema debe permitir al reclutador realizar el ABM (Alta, Baja, Modificación) de ofertas laborales en la plataforma.
* **RF15 — Campos Obligatorios de Oferta**: El sistema debe almacenar para cada oferta laboral su título descriptivo, descripción del puesto, salario estimado, estado y fecha de publicación.
* **RF16 — Vinculación del Creador**: El sistema debe vincular de forma obligatoria cada oferta laboral al identificador del reclutador (`reclutador_id`) responsable de su publicación.
* **RF17 — Ciclo de Vida de la Oferta**: El sistema debe permitir al reclutador gestionar el estado de actividad de la oferta laboral (`ACTIVA`, `INACTIVA`, `FINALIZADA`).
* **RF18 — Habilidades Requeridas**: El sistema debe permitir al reclutador definir y asociar múltiples habilidades técnicas requeridas (`Skills`) para cada oferta laboral.
* **RF19 — Búsqueda y Filtro de Ofertas**: El sistema debe permitir a los postulantes listar todas las ofertas laborales vigentes y realizar búsquedas filtrando por título descriptivo o habilidades requeridas.

---

## 🛠️ Módulo de Habilidades (Catálogo de Skills)

* **RF20 — ABM de Habilidades**: El sistema debe permitir al administrador realizar el ABM (Alta, Baja, Modificación) de las habilidades del catálogo.
* **RF21 — Datos de Habilidades**: El sistema debe almacenar para cada habilidad su nombre único descriptivo (Ej: Java, Spring Boot, React) y su categoría técnica.
* **RF22 — Categorización de Skills**: El sistema debe permitir clasificar cada habilidad bajo las siguientes categorías de la industria: `BACKEND`, `FRONTEND`, `DATABASE`, `CLOUD`.
* **RF23 — Unicidad de Nombre**: El sistema debe garantizar de forma estricta que el nombre de una habilidad técnica sea único en toda la plataforma.

---

## 📝 Módulo de Postulaciones (Gestión de Aplicaciones)

* **RF24 — Postulación a Empleos**: El sistema debe permitir a los postulantes aplicar a ofertas laborales habilitadas y en estado `ACTIVA`.
* **RF25 — Validación de Duplicidad**: El sistema debe validar que un postulante no se encuentre ya inscrito en la misma oferta laboral para evitar duplicidad de solicitudes.
* **RF26 — Registro Temporal**: El sistema debe registrar automáticamente la fecha y hora exacta (`fecha_postulacion`) en la que se efectúa la aplicación.
* **RF27 — Estado Inicial de Postulación**: El sistema debe inicializar el estado del proceso de la postulación de forma automática como `PENDIENTE` al momento del registro.
* **RF28 — Actualización del Estado de Postulación**: El sistema debe permitir al reclutador evaluar el avance del candidato y cambiar el estado del proceso a: `PENDIENTE`, `EN_REVISION`, `RECHAZADO` o `ACEPTADO`.
* **RF29 — Historial de Aplicaciones**: El sistema debe permitir a los postulantes y reclutadores consultar el historial completo de postulaciones realizadas por un candidato o recibidas en una vacante.

---

## 🤖 Módulo de Análisis Inteligente e Inteligencia Artificial (IA)

* **RF30 — Disparo de Análisis**: El sistema debe permitir al reclutador o al sistema disparar el análisis inteligente de compatibilidad sobre una postulación con estado activo.
* **RF31 — Análisis por Modelo de IA**: El sistema debe contrastar a través del motor de IA el currículum y habilidades del postulante frente a la descripción y requerimientos de la oferta laboral seleccionada.
* **RF32 — Cálculo del Match Score**: El sistema debe calcular y guardar en la postulación el puntaje de coincidencia (`match_score`), representado por un valor numérico entero en el rango de 1 a 100.
* **RF33 — Reporte Explicativo (Feedback)**: El sistema debe generar y almacenar un reporte textual detallado (`feedback_ia`) emitido por la IA, explicando los motivos técnicos del puntaje y sugiriendo mejoras.
* **RF34 — Detección Automática de Brechas**: El sistema debe identificar de manera automática las habilidades requeridas por la oferta de empleo que el postulante no tenga asociadas en su perfil, guardándolas como habilidades faltantes (`skills_faltantes`).

---

## ⚙️ Requisitos No Funcionales (RNF)

* **RNF01 — Cifrado de Seguridad**: El sistema debe almacenar las contraseñas de los usuarios de forma cifrada mediante el algoritmo de hash unidireccional de nivel industrial **BCrypt** antes de su persistencia.
* **RNF02 — Desempeño del Análisis**: El tiempo máximo de respuesta del motor de análisis de IA para calcular el score y feedback no debe superar los **5 segundos** por postulación analizada.
* **RNF03-Consistencia de Respuestas de Error**: Toda respuesta de error emitida por la API REST debe ser centralizada mediante `@RestControllerAdvice`, retornando siempre una estructura uniforme en formato JSON que contenga: código de estado HTTP, mensaje descriptivo y la marca de tiempo exacta (`timestamp`).
* **RNF04 — Aislamiento y Encapsulamiento (DTOs)**: El sistema debe prohibir la exposición de entidades JPA directamente en los controladores. Toda transferencia de información entre el cliente y el backend debe procesarse mediante DTOs específicos de entrada (Request) y salida (Response).
* **RNF05 — Transaccionalidad de Operaciones (ACID)**: Los procesos de alta y modificación del dominio (especialmente postulaciones y registro de análisis de IA) deben ejecutarse de forma transaccional mediante la anotación `@Transactional` para garantizar la consistencia relacional y evitar estados corruptos de datos.

Nombre del Proyecto: Proyecto_yeis2 (1.0)

Descripcion: Aplicacion en el cual se puede utilizar Maps

Vulnerabilidades:
1. Certificado de Firma: La aplicación está firmada con un certificado de depuración.

	Severidad: Alta

	Implicación: Las aplicaciones de producción no deben ser distribuidas con certificados de depuración, ya que esto facilita la ingeniería inversa y el acceso no autorizado a la aplicación

2. Compatibilidad con Versiones Vulnerables de Android: La aplicación puede instalar en versiones antiguas de Android (menor a 10) que contienen múltiplos vulnerabilidades no corregidas.

	Severidad: Alta
	Implicación: Esto expone a los usuarios a riesgos de seguridad, ya que esos dispositivos no recibe actualizaciones de seguridad adecuadas

3. Depuración Habilitada: La aplicación tiene habilitada la opción de depuración ().android:debuggable=true

	Severidad: Alta

	Implicación: Esto permite que un atacante puede conectar un depurador y obtener información sensible, facilitando la manipulación del código

4. Permisos de Respaldo de Datos: La aplicación permite el respaldo de datos ().android:allowBackup=true

	Severidad: Advertencia
	
 	Implicación: Usuarios con depuración USB habilitada pueden copiar datos sensibles de la aplicación, lo que podría comprometer la privacidad del usuario

5. Receptor Broadcast Expuesto: Un receptor broadcast está protegido por un permiso cuyo nivel de protección debe ser verificado.

	Severidad: Advertencia

	Implicación: Si el permiso está configurado como normal o peligroso, una aplicación maliciosa podría interactuar con este componente, lo que representa un riesgo potencial

Resumen de puntuacion: El punto general de seguridad para la aplicación es 36/100, clasificada como de alto riesgolo que indica que se requiere atención inmediata para mitigar estas vulnerabilidades.

Mejoras a Realizar 

1. Eliminar el Certificado de Depuration: Reemplaza el certificado de depuración por un certificado de producción, esto previene la ingeniería inversa y el acceso no autorizado a la aplicación.

2. Deshabilitar la Depuración: Cambia el atributo a en el archivo .android:debuggablefalseAndroidManifest.xml, con esto se evita que un atacante puede conectar un depurador y acceder a información sensible.

3. Actualizar el SDK Mínimo: Aumentar el SDK al menos 29 (Android 10).minSdkVersion, ya que esto asegura que la aplicación no se instala en versiones vulnerables de Android que no recibe actualizaciones de seguridad.

4. Deshabilitar Respaldo de Datos: Cambia el atributo a .android:allowBackupfalse, asi previene que los datos sensibles sean copiados a través de ADB cuando la depuración USB está habilitada.

5. Revisar Permisos del Receptor Broadcast: Verifica y ajusta el nivel de protección del permiso asociado al receptor broadcast, asi nos aseguramos de que solo las aplicaciones firmadas con el mismo certificado pueden interactuar con este componente.

6. Implementar Seguridad en la Red: Configuración políticas de seguridad de red para proteger las comunicaciones, esto ayuda a prevenir ataques como MITM (Man-in-the-Middle).

7. Permisos de Auditar: Revisar los permisos solicitados por la aplicación y eliminación los ingresos, asi minimiza el riesgo de abuso de permisos por parte de aplicaciones malas.

8. Realizar Pruebas de Seguridad Regulares: Implementa un programa de pruebas de seguridad periódicas utilizando herramientas automatizadas, con ello se mantiene la seguridad actualizada frente a nuevas vulnerabilidades.

9. Mejorar la Gestión de Errores: Implementa una gestión adecuada de errores y excepciones, asi se evita la exposición accidental de información sensible en mensajes de error.

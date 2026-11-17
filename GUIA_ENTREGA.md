# Publicación y entrega

El proyecto no está publicado en GitHub/GitLab. El ZIP incluye un historial Git local con commits técnicos; no utiliza tu identidad personal.

1. Descomprime el ZIP, incluyendo la carpeta oculta .git si deseas conservar el historial.
2. Configura tu identidad para tus cambios futuros: `git config user.name "Tu nombre"` y `git config user.email "Tu correo"`.
3. Ejecuta el notebook y revisa los resultados. Para registrar modificaciones: `git add .` y `git commit -m "docs: revisar resultados y conclusiones del experimento"`.
4. Crea un repositorio vacío en GitHub/GitLab, sin README inicial.
5. Conecta su URL real: `git remote add origin URL_DE_TU_REPOSITORIO`.
6. Publica con `git push -u origin main` y verifica los permisos de acceso del evaluador.
7. Entrega el enlace del repositorio, según el módulo.

Si tu descompresor omite .git, inicializa con `git init -b main`, `git add .` y `git commit -m "feat: incorporar pipeline base verificado"`.

## Rúbrica del módulo
Pipeline 35%; estructura 20%; dispositivo 15%; arquitectura 15%; validación 10%; documentación 5%.

No subas la presentación ni el notebook docente al repositorio: este proyecto contiene una implementación propia alineada con esos materiales.

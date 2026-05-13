FROM eclipse-temurin:17-jdk-jammy

# configuracion de la aplicacion
ENV APP_HOME=/ecommerce-app
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME

#puerto a exponer
EXPOSE 8084

# copiar el jar (nombre fijo de la version)
COPY target/ecommerce-*.jar app.jar

# usuario no-root para seguridad
RUN useradd -m appuser && chown -R appuser:appuser $APP_HOME
USER appuser

# salud del sistema interno
HEALTHCHECK --interval=30s --timeout=3s \
  CMD curl -f http://localhost:8084/actuator/health || exit 1

# comando de ejecucion
ENTRYPOINT ["java", "-jar", "app.jar"]
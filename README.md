# Despliegue de Aplicación con WordPress y MySQL usando Kubernetes y Helm

## Descripción del Proyecto

En este proyecto, he desplegado una aplicación WordPress con una base de datos MySQL utilizando Kubernetes y Helm. El proceso comenzó con la creación del clúster y posteriormente transformé la configuración en un Chart de Helm. Esto requirió reestructurar varios componentes y generar templates, junto con una serie de modificaciones para garantizar el correcto despliegue.

## Estructura del Proyecto


```

sergichart/
├── charts/
├── templates/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── mysql-statefulset.yaml
│   ├── mysql-service.yaml
│   ├── mysql-pvc.yaml
│   ├── ingress.yaml
│   ├── hpa.yaml
│   └── mysql-secret.yaml
├── Chart.yaml
├── values.yaml
└── .helmignore

```

## Pasos Realizados

1. **Inicialización del Clúster**  
   Inicié Minikube con tres nodos, aunque durante el desarrollo comprobé que con dos nodos era suficiente.  
   ![Minikube](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/CreaciponMinikube.png?raw=true)

3. **Preparación del Entorno**  
   - Creé una carpeta para almacenar el proyecto.
   - Definí un *namespace* llamado `kuberkid` donde se recrearán todos los recursos.

4. **Gestión de Secretos**  
   - Generé los *secrets* necesarios para el despliegue de WordPress y MySQL.
   - Incorporé estos *secrets* en las configuraciones de los deployments correspondientes.  
   ![Generación de los Secrets](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/Generamos%20los%20Secret.png?raw=true)  
   ![Introducción de los Secrets](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/Introducimos%20los%20secrets.png?raw=true)

5. **Configuración de Servicios**  
   - Configuré los servicios necesarios para la comunicación entre los pods.
   - Utilicé `NodePort` para exponer WordPress y `ClusterIP` para MySQL.  
   ![Configuración de Servicios](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/servicios.png?raw=true)

6. **Verificación de MySQL**  
   - Verifiqué que MySQL estuviera corriendo correctamente.
   - Asigné privilegios al usuario `sergio` para gestionar la base de datos.  
   ![Verificación de MySQL y Privilegios](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/verificamos%20que%20mysql%20y%20privilegios.png?raw=true)  
   ![WordPress Corriendo](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/wordpress.png?raw=true)

7. **Almacenamiento Persistente**  
   - Creé un *PersistentVolume* (PV) y un *PersistentVolumeClaim* (PVC).
   - Monté el volumen en el deployment y comprobé su correcta construcción.  
   ![PersistentVolume](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/pv.png?raw=true)  
   ![Construcción del Volumen](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/construidovolumen.png?raw=true)  
   ![Montaje en el Deployment](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/montaje%20deploy.png?raw=true)

8. **Pruebas de Funcionamiento**  
   - Realicé pruebas para asegurar que la aplicación funcionara correctamente.  
   ![Prueba de Persistencia](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/prueba%20de%20persistencia.png?raw=true)

  



11. **Construcción del Chart de Helm**  
    - Con todos los archivos configurados, construí un Chart de Helm para facilitar el despliegue de la aplicación.  
    ![Chart de Helm](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/helmen.png?raw=true)

10. **Exposición de la Aplicación**  
    - Activé *Ingress* para exponer la aplicación al exterior.  
    ![Configuración de Ingress](https://github.com/KeepCodingCloudDevops11/Sergio-Kubernetes/blob/master/imagenes/ingress.png?raw=true)

## Herramientas Utilizadas


- **Mobaxterm**: Para la gestión de conexiones y terminal.
- **Visual Studio Code**: Para la edición y gestión del código.


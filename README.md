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
   Inicié Minikube  
   ![Minikube](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/inicio%20minikube.png)


2. **Gestión de Secretos**  
   - Generé los *secrets* necesarios para el despliegue de WordPress y MySQL en base64.
    ![Generación de los Secrets](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/mysecret.png)  


3. **Configuración de Servicios**  
   - Configuré los servicios necesarios para la comunicación entre los pods estableciendo los valores en el archivo values.
   - Utilicé `NodePort` para exponer WordPress y `ClusterIP` para MySQL.  
   ![Configuración de Servicios](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/mysqlservice.png)
   ![Configuración de Servicios](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/mysqlservice.png)


4. **Almacenamiento Persistente**  
   - Creé un *PersistentVolume* (PV) y un *PersistentVolumeClaim* (PVC).
   - Especificaciones en values.yalm.  
   ![PersistentVolume](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/persistencevolumen.png)  
   ![Values](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/persistspec.png)


5. **Creación del autoescaling especificación en value**
   ![Scaling al 75%](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/autoscaling.png)
   ![Values](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/autoescalingspec.png)


6. **Construcción del Chart de Helm**  
    - Con todos los archivos configurados, construí un Chart de Helm para facilitar el despliegue de la aplicación y comprobamos.   
    ![Chart de Helm](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/helminstall.png)
    ![Comprobación](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/comprobacionheml.png)
  

7. **Pruebas de Funcionamiento**
    ![Port-forward](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/Prueba.png)
    ![Wordpress](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/wordpress.png)
   
   
  





11. **Exposición de la Aplicación**  
    - Activé *Ingress* para exponer la aplicación al exterior.  
    ![Configuración de Ingress](https://github.com/SergiMPorto/kubernetes/blob/master/imagenes/PruebaIngress.png)

## Herramientas Utilizadas


- **Mobaxterm**: Para la gestión de conexiones y terminal.
- **Visual Studio Code**: Para la edición y gestión del código.


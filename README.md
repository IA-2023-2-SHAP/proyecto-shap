# Proyecto SHAP
Proyecto para la asignatura de Introducción de Inteligencia Artificial 2023-1 de la Universidad Nacional de Colombia.

## Miembros
* Samuel Camilo Burgos Rojas <sburgos@unal.edu.co>
* Mateo Alejandro Diaz Munoz <maadiazmu@unal.edu.co>
* Fredy Andres Rosero Cristancho <faroseroc@unal.edu.co>


## Contenido
1. Proyecto ¿que es lo que se quiere hacer? (Fredy) [1min]
2. Introducción a teoría de juegos (Fredy) [1min]
3. Explicador del modelo lineal (Fredy)[5min]
  * Dataset y modelo [1min]
  * Explainer [2min]
  * Gráficas [2min]
    * Dependencia parcial [24sg]
    * Wattefall [24sg]
    * force_plot [24sg]
    * summary_plot [1min]
    * beeswarm [24sg]
4. Modelos de radomForest
   1. Explicar los que se va a usar enm los ejemplso de Diabetes e Iris (Samuel)[6min]
      1. Explicar contexto de dataset (columnas) [4min]
         1. Diabetes
         2. Iris
         3. Spam(opcional)
      2. Nombrar dependencias [1min]
         1. Sklearn
         2. Shap
            1. Explainer
            2. Gráficas
      3. Nombrar los modelos [1min]
   2. Explicar el código y la gráficas (Mateo)[6min]
      1. Cada una de las partes del código [2min]
      2. Cada una de las gráficas. [40sg] por gráfica
5. Conclusiones (Mateo)[1min]

## Jupyer Notebook en Docker

Para lanzar Jupiter Notebook en Docker se puede usar el siguiente comando:
~~~bash
$ docker run -it -p 8888:8888 -v "${PWD}":/home/jovyan/work --name jupyter jupyter/scipy-notebook
~~~

Para lanzar el contenedor nuevamente en modo interactivo se puede usar el siguiente comando:
~~~bash
$ docker start -i jupyter
~~~

Para conectarnos a la shell del contenedor (por ejemplo para instalar mas cosas) podemos usar el siguiente comando:
~~~bash
$ docker exec -it jupyter bash
~~~

## Referencias

[^1]: https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html

[^2]: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook
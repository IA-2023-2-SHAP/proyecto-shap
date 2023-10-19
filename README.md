# Proyecto SHAP
Proyecto para la asignatura de Introducción de Inteligencia Artificial 2023-1 de la Universidad Nacional de Colombia.

## Miembros
* Samuel Camilo Burgos Rojas <sburgos@unal.edu.co>
* Mateo Alejandro Diaz Munoz <maadiazmu@unal.edu.co>
* Fredy Andres Rosero Cristancho <faroseroc@unal.edu.co>

## Jupyer Notebook en Docker

Para lanzar Jupiter Notebook en Docker se puede usar el siguiente comando:
~~~bash
$ docker run -it -p 8888:8888 -v "${PWD}":/home/jovyan/work --name jupyter jupyter/scipy-notebook
~~~

Para conectarnos a la shell del contenedor podemos usar el siguiente comando:
~~~bash
$ docker exec -it jupyter bash
~~~

## Referencias

[^1]: https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html

[^2]: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook
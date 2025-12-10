# 🔋 Actividad Práctica: "El Indicador de Batería Inteligente"

## Objetivo
 Crear un widget visual que represente 5 niveles de carga. El alumno deberá usar un bucle numérico (@for) para generar las barras automáticamente y un condicional (@if) para decidir si la barra es roja (batería baja) o verde (batería alta).

 ### 1. Estructura de Carpetas
 Replica la estructura estándar. Tómate el tiempo de crear los archivos vacíos primero.

```text
/battery-project
  index.html
  /scss
    main.scss
    /abstracts
       _variables.scss    (Colores base)
       _functions.scss    (Matemáticas simples)
       _mixins.scss       (Lógica de colores)
    /base
       _reset.scss        (Centrado en pantalla)
    /components
       _battery.scss      (El componente principal y el bucle)
```

### 2. El HTML (Ya listo)
Copia este HTML. Nota que tenemos un contenedor .battery y 5 divs hijos. Importante: Fíjate que los hijos no tienen clases diferenciadoras (como --1, --2). ¡Tu trabajo será generarlas con SASS!

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Battery Level</title>
    <link rel="stylesheet" href="css/main.css">
</head>
<body>

    <main class="battery">
        <div class="battery__bar battery__bar--1"></div>
        <div class="battery__bar battery__bar--2"></div>
        <div class="battery__bar battery__bar--3"></div>
        <div class="battery__bar battery__bar--4"></div>
        <div class="battery__bar battery__bar--5"></div>
    </main>

</body>
</html>
```

### 3. Instrucciones Paso a Paso

#### Paso A: Variables (abstracts/_variables.scss)

Define:

1) Un tamaño base: $bar-height: 50px;.

2) Un ancho base: $bar-width: 20px;.

3) Dos colores: $color-danger (rojo) y $color-success (verde).

#### Paso B: Matemáticas Simples (abstracts/_functions.scss)

Crea una función llamada calc-height.

* Debe recibir un número (el nivel de la barra, por ejemplo, 3).

* Debe devolver la altura base multiplicada por ese número.

* Lógica: return $bar-height * $numero.

#### Paso C: Lógica Condicional (abstracts/_mixins.scss)

* Crea un mixin llamado set-color.

* Debe recibir un argumento: $level (un número del 1 al 5).

* Usa @if:

    * Si el $level es menor o igual a 2, el fondo debe ser $color-danger.

    * @else (si es mayor a 2), el fondo debe ser $color-success.

#### Paso D: El Bucle (components/_battery.scss)

Este es el paso crucial.

1) Estila el contenedor .battery para que sea un contenedor flex (display: flex, gap: 10px, align-items: flex-end). Esto hará que las barras se alineen abajo como un gráfico.

2) Estila la clase base .battery__bar con el ancho base ($bar-width).

3) Genera las variantes con @for:

* Crea un bucle que vaya desde $i de 1 hasta 5.

* Dentro del bucle, genera el selector: &--#{$i}.

* Dentro de ese selector:
    1) Llama a tu función matemática para establecer la height. (La barra 1 será baja, la 5 será alta).

    2) Llama a tu mixin set-color($i) pasándole el número actual del bucle.

#### Paso E: Unificar (main.scss)

Importa los archivos en el orden correcto para que las variables existan antes de ser usadas.


### 4. Resultado Esperado
Si lo haces bien:

1) Verás 5 barras alineadas horizontalmente.

2) Tendrán alturas escalonadas (como una escalera o señal de celular).

3) Las dos primeras barras (1 y 2) serán Rojas.

4) Las tres últimas (3, 4 y 5) serán Verdes.

5) Todo esto generado automáticamente, sin escribir background: red cinco veces

### 5. Forma de Entrega
debera crea un repositorio para esta activdad y exponerlo usando github pages.
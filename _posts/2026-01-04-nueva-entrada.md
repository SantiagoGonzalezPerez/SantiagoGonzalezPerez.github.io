---
layout: post
title: "Generación de la APK de la app móvil"
date: 2026-01-04 12:00:00 +0100
excerpt: "Construcción de la build de desarrollo y la APK de la app móvil para no depender de la ejecución por ordenador."
---

<style>
    .imagen {
        text-align: center;
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 75%;
        height: 75%;
    }

    .imagen2 {
        text-align: center;
        display: block;
        margin-left: auto;
        margin-right: auto;
        width: 40%;
        height: 40%;
    }

    .imagenes {
        display: flex;
        justify-content: center; /* Centra las imágenes horizontalmente */
        gap: 5rem; /* Espacio entre las imágenes */
        align-items: center; /* Alinea verticalmente las imágenes */
    }

    .pantalla {
        width: 17%; /* Ajusta el ancho de cada imagen */
        height: auto;
    }
</style>

Tal y como escribí en la <a href="https://santiagogonzalezperez.github.io/2025/12/15/bienvenido-a-mi-blog.html">anterior entrada del blog</a>, logré externalizar el código generado por la IA **Claude** para desarrollar mi proyecto de aplicación móvil, tanto para introducir cambios en mi editor de código como para ejecutar y visualizar la app en mi dispositivo móvil, esto último gracias al uso de **Expo Go**. A medida que avanzaba en el desarrollo de la misma introduciendo las funcionalidades base que tenía pensado para el PVM de la app, aumentaba el tiempo dedicado al *testing* y la consecuente localización y arreglo de pequeños errores. En este sentido me resultaba crucial contar con segundas opiniones y usos, necesitaba pues ejecutar la aplicación en dispositivos diferentes al mío personal. Tras informarme me fijé el siguiente gran paso: generar la APK de mi app.

## Romper la dependencia con la terminal

Para poder desarrollar la APK propiamente dicha era necesario generar previamente una *build* de desarrollo, siendo esta una versión compilada y ejecutable del código fuente de la app, creada para la realización de pruebas, introducción de modificaciones, verificación y depuración de flujos de funciones... Hasta el momento no existía una *build* de desarrollo al uso dado que la integridad del código era ejecutado vía terminal para poder ser visualizado y usado. Esta circunstancia, razón de la existencia de la presente entrada, constituía un gran problema en lo que respecta al desarrollo y ejecución de la app dado que hacía depender esta al 100% del ordenador, la máquina con la terminal desde la que introducía los comandos para generar el código QR y ejecutar y visualizar la app usando **Expo Go**.

<img src="/assets/images/appavanzada.png" class="imagen" alt="Vista de una versión de la aplicación más avanzada"/>

Dado que usaba la aplicación anteriormente mencionada para ejecutar y visualizar mi app, **Claude** me recomendó generar un **EAS (Expo Application Services) build** como base de la *build* de proyecto: un conjunto de servicios en la nube de **Expo** que permite la compilación de código sin necesidad de tener instalado localmente **Android Studio** o similares. Para ello el primer paso consistía en instalar **EAS CLI** vía terminal con la siguiente secuencia de comandos:

`nnpm install -g eas-cli`<br>
`eas login`<br>
`eas build:configure`<br>

Como se puede observar antes de ejecutar el comando que realmente genera la *build* era necesario indicar previamente el usuario y contraseña de la cuenta de **Expo**. 

## Destino: APK

La generación de la *build* de desarrollo lleva implícito la generación de un nuevo archivo para el proyecto: eas.json; el cual reúne los perfiles de compilación necesarios, en mi caso **Android**, por el momento. Para construir la **APK** usé el siguiente comando:

`eas build --profile preview --platform android`<br>

El proceso puede llegar a durar varios minutos, algo positivo es que en la terminal se genera una **URL** que redirige al panel de usuario en el sitio web de **Expo** para poder seguir el proceso de una manera más visual y cómoda, permitiendo ver los detalles de cada log, posibles fallos...

<img src="/assets/images/vistaexpodev.png" class="imagen" alt="Vista del proyecto en el panel de usuario de Expo.dev"/>

## Problemas con integraciones

En mi caso tuve que hacer frente a varios problemas en la generación de la **APK** al no generarse correctamente dada la inconexión con algunas librerías que el código base de la app usa para poder realizar ciertas funciones. Tras investigar un poco más resolví añadiendo la configuración de compilación explícita en el archivo app.json. Hecho esto volví a intentar generar la **APK**, limpiando previamente la caché del proyecto con el comando:

`eas build --profile preview --platform android --clear-cache`<br>

## Resultado

Como resultado obtuve la **APK** de mi proyecto de aplicación, la cual instalé en el móvil escaneando el código QR que vía terminal se generó al crearse la **APK** (a la par que un link). Además, compartí el link para que otra persona pudiera probar desde su dispositivo la aplicación. Todo ello con el ordenador apagado y sin haber introducido previamente el comando que usaba para ejecutar y visualizar la app en **Expo Go**. El hecho de no depender del uso de la terminal para poder visualizar la app y usarla resulta un gran avance y agilización del propio proceso de desarrollo, así como la posibilidad de que otras personas puedan usarla y me transmitan su sensación, sugerencias, fallos que encuentren...

<div class="imagenes">
    <img src="/assets/images/apkinstalada.png" class="pantalla" alt="Vista de la app instalada en mi móvil"/>
    <img src="/assets/images/vistappteresa.png" class="pantalla" alt="Vista de la app ejecutada en otro móvil"/>
</div>

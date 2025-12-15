---
layout: post
title: "Deploy de prototipo de app en móvil"
date: 2024-05-15 10:00:00 -0600
excerpt: "Primera toma de contacto con el desarrollo de apps móviles; desarrollo de un prototipo inicial y visualización en un dispositivo móvil real."
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
La idea de desarrollar una aplicación de móvil siempre ha rondado mi cabeza y, por mucho que tuviera el proyecto de realizarla anotado, jamás me puse a ello, al menos hasta ahora. Siendo plenamente consciente de mi falta de conocimientos y experiencia en este sentido, resolví aprovechar los avances de la IA en materia de *coding* para poder emprender de una vez por todas el proyecto. Tras la identificación de los principales agentes de IA e informarme sobre *vibe coding* me decidí por usar **Claude**.

## Sobre Claude

**Claude** es un modelo de inteligencia artificial conversacional desarrollado por **Anthropic** que, al igual que otros modelos IA tales como **Chat GPT** o **Gemini**, permite la comprensión y generación de texto, así como el análisis de información compleja o la asistencia en una gran cantidad y diversidad de tareas creativas y profesionales. Como características distintivas de este modelo, y razones las cuales me han hecho decantarme por él para trabajar en el proyecto de app, tenemos su enfoque en seguridad, mayor habilidad para entender código y programar, vista de editor de código en su versión base...

<img src="/assets/images/claudeig.png" class="imagen" alt="Interfaz de la IA Claude"/>

## Primeros pasos del desarrollo

Comencé transmitiéndole a **Claude** la idea de aplicación móvil que tenía, indicandole cuál sería su principal funcionalidad, el problema que pretendía solucionar, ciertas pantallas básicas que la app debería tener... Inmediatamente y previo a la generación de código alguno, me sugirió la opción de desarrollo más viable para el tipo de aplicación que deseaba crear: **React Native** con **Expo**. *Framework* de código abierto capaz de crear aplicaciones nativas para **iOS** y **Android**. Tras confirmar, **Claude** generó el código base inicial de prueba.

<img src="/assets/images/appweb.png" class="imagen" alt="Vista de la app en el navegador"/>

Dicho código era funcional y visible dentro de la interfaz de **Claude**, sin embargo, lo que yo deseaba era extraer dicho código para guardarlo en mi ordenador y tener a disposición para poder editarlo, ejecutarlo externamente… He aquí dónde apareció el segundo problema mayor: ¿Cómo visualizar la app en un dispositivo móvil?

## Extraer el código

Para ello utilizaría **Node.js**, el cual tuve que instalar desde cero y, posteriormente, crear el proyecto vía terminal; en mi caso usé **Git Bash** por estar familiarizado con él y darme menos problemas en dependencias y permisos que la **cmd de Windows**.

`npm create vite@latest nombreapp -- --template react`<br>
`cd nombreapp`<br>
`npm install`<br>
`npm install lucide-react`<br>

Acto seguido copié y pegué el código del prototipo inicial de app que la IA había generado en un archivo **.js**, el cual ubiqué dentro de la carpeta del proyecto. Hasta el momento, si ejecutaba el comando mostrado a continuación, la app era visible únicamente vía web en mi ordenador.

`npm run dev`<br>

Para lograr el visualizado de la app en un dispositivo móvil era necesario el uso de una tecnología más, en mi caso me serví de **Expo Go/CLI** (por recomendación de la IA), el cuál también tuve que instalar desde cero. Una vez logrado creé el proyecto propio vía terminal mediante el siguiente comando:

`npx create-expo-app nombreapp`<br>

Lo último antes de lograr la visualización de la app en móvil era adaptar el código existente a su versión en **React**, de lo cuál se encargó **Claude**; básicamente una actualización del ya existente archivo **.js** con el copia y pega del código actualizado.

## Visualización en un dispositivo móvil real

Ahora sí, todo estaba listo para ejecutar la aplicación vía el comando:

`npx expo start`<br>

Dicho comando genera en la terminal un mensaje de gran tamaño que, entre otra mucha información, muestra un código QR y una serie de comandos adicionales para llevar a cabo ciertas acciones. 

<img src="/assets/images/QRcodecomando.png" class="imagen2" alt="Respuesta de comando con código QR"/>

El código QR es lo que actúa como portal de entrada a la app, el cual debe ser escaneado desde la propia aplicación de **Expo Go** (la cual debemos tener instalada en el dispositivo móvil donde deseemos ejecutar y visualizar nuestra app).

<div class="imagenes">
    <img src="/assets/images/pantalla1.png" class="pantalla" alt="Vista de la pantalla de carga en el dispositivo móvil"/>
    <img src="/assets/images/pantalla2.png" class="pantalla" alt="Vista de la pantalla principal de la app en el dispositivo móvi"/>
</div>

Gracias al uso de la IA he podido desarrollar, sin muchos conocimientos y tiempo dedicado, un prototipo muy rudimentario pero funcional de mi proyecto de app, veremos si actúa igual de bien y permite añadirle interacción y otras funcionalidades en el futuro.

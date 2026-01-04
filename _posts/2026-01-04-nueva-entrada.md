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

Tal y como escribí en la <a href="https://santiagogonzalezperez.github.io/2025/12/15/bienvenido-a-mi-blog.html" target="_blank" rel="noopenernoreferrer">anterior entrada del blog</a>, logré externalizar el código generado por la IA Claude para desarrollar mi proyecto de aplicación móvil, tanto para introducir cambios en mi editor de código como para ejecutar y visualizar la app en mi dispositivo móvil, esto último gracias al uso de Expo Go. A medida que avanzaba en el desarrollo de la misma introduciendo las funcionalidades base que tenía pensado para el PVM de la app, aumentaba el tiempo dedicado al testing y la consecuente localización y arreglo de pequeños errores. En este sentido me resultaba crucial contar con segundas opiniones y usos, necesitaba pues ejecutar la aplicación en dispositivos diferentes al mío personal. Tras informarme me fijé el siguiente gran paso: generar la APK de mi app.

## Introducción

Aquí puedes comenzar a escribir el contenido de tu nueva entrada.

Recuerda que puedes usar **Markdown** para dar formato al texto, añadir imágenes y enlaces.

# Descripción

Este proyecto es usado como ejemplo de ci con pipeline y webhooks(en github) y [ngrook](https://ngrok.com/), con el objetivo de conectar y notificar el servidor de ci (jenkins),
con el repositorio remoto de manera automatico basado en eventos (push de commits, pull request entre otros) y ejecutar un pipeline cuando se envie la notificacion (con webhooks).

![arquitectura.png](assets/arquitectura.png)

## Paso a paso

1. Instalacion de ngrook ya que para usar webhooks se debe tener nuestro servidor de ci visible de internet y esta herramienta lo permite usando un proxy,
  para instalar usar https://ngrok.com/download.
```shell
# descargar via snap
 sudo snap install ngrok
```
2. Crear cuenta con ngrook se permite apartir de github
3. Seguir pasos de la pagina de ngrook una vez logueada su cuenta (copiar token, iniciar ngrook(se debe iniciar en el puerto donde corra el servidor de ci)).
4. Ahora se debera ir al webhook en github, para ello ir al repositorio especifico > settings > webhooks > add webhooks
5. Ahora se debe configurar el webhook, en payload url indicar la url https que otorga ngrok(es informacion sensible) via terminal a esto se le agrega el sufijo
   /github-webhook/ ej: https://xyz/github-webhook/, content type -> json y por ultimo indicar el evento a notificar en este caso seran commits, pero se puede
   indicar cualquier tipo de evento, pull request, creacion de ramas, etc. lo demas se deja por defecto.
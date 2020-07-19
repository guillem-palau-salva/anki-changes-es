# Problemas conocidos

## Aceleración de hardware y problemas de inicio en Windows/Linux

La aceleración de hardware por defecto está desactivada en Windows y Linux. Habilitándolo
en la pantalla de preferencias y reiniciando Anki puede hacer que la interfaz de Anki
más receptiva, pero algunos usuarios pueden experimentar barras de menú faltantes, ventanas en blanco
o se bloquee cuando está habilitado.

En Windows si no puede acceder a la pantalla de preferencias de Anki y
reiniciar Anki varias veces no ayuda, es posible que deba ajustar el controlador
de gráficos manualmente. Puede hacerlo iniciando cmd.exe y
escribiendo lo siguiente:

    echo auto > %APPDATA%\Anki2\gldriver

Puede probar tres configuraciones: 'auto', 'angle' y 'software'.
Si tiene problemas cuando la aceleración de hardware está activada y
desactivado en las preferencias, vale la pena intentar 'angle'.

En Linux, puede escribir 'auto' o 'software' en
~ .local/share/Anki2/gldriver para ajustar el controlador. Tenga en cuenta que si
estás usando nouveau, se sabe que tiene errores y solo admite
modo de software.

## Velocidad de la interfaz

Incluso si habilita la aceleración de hardware como se mencionó anteriormente, puede
encontrar a Anki tarde más en iniciar y mostrar nuevas ventanas, especialmente si
su ordenador no es la más rápido. Esto es a causa del uso de una nuevo
kit de herramientas web, que trae nuevas características y mejoras de seguridad, pero
desafortunadamente requeire más recursos. El kit de herramientas web de versiones más
antiguas de Anki se ha abandonado, por lo que ya no es un
opción para futuros lanzamientos.

## Pantallas en blanco y eGPU en Mac

Si experimenta pantallas en blanco cuando usa una tarjeta gráfica externa en
Mac, puede usar la versión -alternate (alternativa) del sitio de descarga,
o ctrl + clic en la aplicación Anki, haga clic en _"Obtener información"_ y active la opción _"preferir
eGPU"_.

## Atajos de teclado

El acceso directo para deshacer es diferente en la versión alternativa debido a un problema
con el juego de herramientas. Puede descubrir el acceso directo alternativo mirando
el menú _Editar_ de la pantalla principal.

En macOS, la compilación alternativa no admite algunos accesos directos como
cmd + izquierda/derecha al editar tarjetas. Fn + izquierda/derecha funciona en su lugar.
También puede usar una herramienta de terceros como BetterTouchTool o Karabiner para
interceptar la combinación de teclas cmd + izquierda/derecha cuando la escriba en Anki, y
haga que se reescriba automáticamente para usar la tecla de función en su lugar.

## Problemas de copiar y pegar en Windows

Si tiene problemas al copiar y pegar en Windows,
compruebe si está ejecutando otros programas en su ordenador que
monitoreen el portapapeles, como programas de diccionario, administradores de portapapeles
o herramientas de recortes. El kit de herramientas que usa Anki puede tener problemas cuando
los programas se están ejecutando.

## Fcitx en Linux

La compilación estándar de Anki incluye soporte fcitx, pero puede no funcionar en
todas las distribuciones. Si no puede usar fcitx, puede ejecutar
Anki desde el código fuente, o cambie a un método de entrada diferente.

## Tamano del texto

Si encuentra que el texto es del tamaño incorrecto, hay dos
variables que puede probar:

- ANKI\_NOHIGHDPI=1 desactivará parte del soporte de alta resolución de Qt.

- ANKI\_WEBSCALE=1 alterará la escala de las vistas web de Anki (como el
     lista de mazos, pantalla de estudio, etc.), dejando elementos de interfaz como
     la barra de menú solo. Reemplace 1 con la escala deseada, así como 1.5 o
     0.75.

En Windows, puede agregarlos a un archivo por lotes (batch) para que sea más fácil iniciar
Anki. Por ejemplo, cree un archivo llamado _startanki.bat_ en su escritorio
con el siguiente texto:

    set ANKI_WEBSCALE=0.75
    start "Anki" "C:\Program Files\Anki\anki"



## Errores SSL

Algunas redes laborales y escolares interceptan el tráfico de Internet, y esto
puede causar errores al sincronizar y descargar complementos. Puede prevenir
los errores se producen al establecer la variable ambiental
"ANKI\_NOVERIFYSSL" a "1".

Cuando habilite esta opción, le está diciendo a Anki que no verifique que
en realidad está hablando con AnkiWeb. Esto significa que no solo su trabajo o
escuela, pero también un mal actor en la red local puede ser capaz de
interceptar su tráfico de sincronización.

En Windows, puede crear un archivo .bat como se describe en la sección
Tamaño del texto más arriba.

En Mac, puede abrir Terminal.app, luego inicie Anki con el siguiente
mando:

    ANKI_NOVERIFYSSL=1 open /Applications/Anki.app

En Linux, use lo siguiente en una terminal:

    ANKI_NOVERIFYSSL=1 anki

Una vez que haya iniciado Anki con SSL deshabilitado, puede descargar el
siguiente complemento para que el cambio sea permanente:

<https://ankiweb.net/shared/info/878367706>



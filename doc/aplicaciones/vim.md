Se puede copiar dentro de vim haciendo el comando CTRL-v, lo que se conoce como
"poner el modo de copia" dentro de vim. En vez de copiar, puede pegar con el
comando CTRL-v p, lo que se conoce como "poner el modo de pegar". Se puede
copiar, copiar e insertar en vim usando el comando CTRL-v y luego el comando i
para insertar.

Si desea desactivar o habilitar los comentarios en vim, use el comando :set
comment .
Si desea desactivar los comentarios, escriba:
:set comment=n
Si desea habilitar los comentarios, escriba:
:set comment=s
Se puede desactivar temporalmente los comentarios con el comando :set comment=0
Se puede desactivar temporalmente los comentarios en la pantalla con el comando
:set nocom.
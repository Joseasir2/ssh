# Como conectarse a un usuario de otra máquina por media de claves públicas y privadas

## 1. Generar clave

Primero tendremos que generar una clave con el comando ssh-keygen: (se obvia que primero tendremos que tener instalado ssh)

$ ssh-keygen

Una vez lancemos este comando nos dirá que lo guardará en una ruta oculta "/.ssh", esta ruta se puede modificar. Le daremos a enter y nos dirá si queremos una frase de seguridad, como solo queremos una contraseña generada por ssh no pondremos nada.

# IMPORTANTE, no poner espacios en la frase clave para no tener problemas

## 2. Compartir clave y conectarnos

Si nos fijamos y vamos a la carpeta oculta que es en la siguiente ruta: */home/[carpeta personal]/.ssh* dentro tendremos dos archivos, el de clave pública [id_rsa.pub] y la privada [id_rsa]. Nosotros tendremos que compartir a nuestro compañero la clave pública en el archivo id_rsa.pub y para ello usaremos el siguiente comando:

$ ssh-copy-id [nombre_usuario]@[ip_del_compañero]

Y con esto ya podremos conectarnos a la máquina de nuestro compañero poniendo

$ ssh [nombre_usuario]@[ip_usuario]


-----------------------------------------------------------------


# Configurar el acceso ssh en el GitHub

## Crear clave para GitHub

Iremos a "Settings" de nuestra cuenta de GitHub y iremos al apartado de SSH. Una vez ahí le daremos a "add SSH key", nos saldrá un rectángulo donde tendremos que epgar nuestra clave pública ssh. Para ello la consultaremos en la carpeta oculta ".ssh/" y tendremos que pegar el contendio del archivo "id_rsa.pub" en el rectángulo y ya se habrá creado una clave ssh para neustro GitHub.

## Añadir repositorio con SSH

Iremos al repositorio que vayamos a usar y copiaremos la URL que nos da nuestro repositorio de GitHub, debería ser algo así:

https://github.com/Joseasir2/ssh.git

Ahora en una consola pondremos el siguiente comando con esa URL:

$ ssh -T git@github.com

$ ssh clone git@github.com:Joseasir2/[nombre repositorio].git

Y con esto ya estaría, hariamos:

$ git add [nombre archivo]
$ git commit -m "first commit"
$ git push origin main




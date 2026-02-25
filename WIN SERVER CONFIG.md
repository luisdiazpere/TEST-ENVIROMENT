


# AD DOMAIN: Luis.Diaz
 - DNS CONFIG 
<img width="1156" height="294" alt="image" src="https://github.com/user-attachments/assets/819c3868-a6eb-4b07-a4fa-e92c81ad86f1" />
<img width="396" height="471" alt="image" src="https://github.com/user-attachments/assets/d03270be-0ce7-4256-99f3-78766ee9fcbf" />

-DHCP CONFIG

| DHCP POOL |
|-------|
| 10.10.110.50-75 /24 | 


| IP reservada | HOST |
|-------|--------------|
| 10.10.110.2| OPN(Firewall) |
| 10.10.110.5| HTOP(Win Server) |
| 10.10.110.6| SPL(Ubunut server) |


- AD User and computers
<img width="327" height="295" alt="image" src="https://github.com/user-attachments/assets/a741ce6b-86d0-40a8-95f6-13ff1464e2b8" />


Este lab cuenta con 5 OU para deparamentos de "produccion" que cuentan con 5 usuarios cada una Direccion Administrativa, Direccion de Comunicacines, Direccion de Gestion Humana, Direccion de Tecnologia y Direccion legal y 2 de pruebas y app y GPO que serian FORENSE Y MOFONE



- SHARED FOLDER

  <img width="574" height="180" alt="image" src="https://github.com/user-attachments/assets/5aaeeecb-186d-4fe2-b05b-463557cf1f6c" />

  En este entorno simulado se comparte 3 carpetas que cumplen el siguiente proposito:
  
| FOLDER | FUNCION |
|-------|--------------|
| APPS | En esta carpeta se encuentran todos los instaladores de las app que se usarian en la empresa. |
| FOLDERS | Aqui se encuentran los folders respectivos de cada Deparamentos/Direccion |
| USER_HOME | Este es una carpeta que es requeriada para un politica de redirecion de folder. Más detealle en (ponga el href )|

- Splunk Universal forwader
Splunk es un software que permite analizar y organizar data obtenidad por sistemas , en el caso de este lab sera utilizado para verificar logs de nuestros servicios esto siendo posible con Splunk Universal Forwarder que nos permite ingestar datos a splunk.

Dicho lo anterior la configuracion del Universal Forwader es la siguiente:

<img width="329" height="230" alt="image" src="https://github.com/user-attachments/assets/44d81d50-a29b-4fd1-9c13-269e6daa0f53" />

Cualquier PC cliente tiene que tener acceso al puerto indicado al momento de instalar el agente, en este caso esta por default que es el 9997.

A continuacion se enseñara que data se esta ingestando:

<img width="263" height="254" alt="image" src="https://github.com/user-attachments/assets/768455ec-f0c6-4fb4-8b0f-4f7de412e884" />

En el caso de este lab estaremos usando splunk para verificar logs de seguridad solamente estamos ingestando logs de seguridad y de sistema.



# GPO 

A continuacion se desglosara que hace cada GPO y donde esta siendo aplicada:

<img width="281" height="263" alt="image" src="https://github.com/user-attachments/assets/4a89671c-f4a7-4ab4-afd4-85f25bf76a39" />

| GPO        | ÁMBITO                  | FUNCIÓN TÉCNICA                                                              |
| ---------- | ----------------------- | ---------------------------------------------------------------------------- |
| ADM        | Dominio completo        | Password Policy, Account Lockout, Login Policies, Fondo corporativo estándar |
| APP        | Todos los departamentos | Instalación automatizada de aplicaciones base vía GPO                        |
| CM         | Todos los dispositivos  | Restricción de acceso a `cmd.exe` para usuarios fuera del grupo Tecnología   |
| COPILOT    | Todos los departamentos | Bloqueo de ejecución de Microsoft Copilot (versión nativa y externa)         |
| FOLDERS    | Todos los departamentos | Mapeo automático de shared folders basado en grupos de seguridad             |
| FONDO      | OU MOFONE y FORENSE     | Fondo diferenciado para entorno de laboratorio                               |
| HORA       | Dominio completo        | Sincronización NTP desde servidor del dominio                                |
| RUN        | Todos los departamentos | Control del acceso a `run.exe` para usuarios de bajo privilegio              |
| SI         | Entorno de pruebas      | Restricción de acceso al disco C:\                                           |
| TEST       | Entorno de pruebas      | Eliminación de perfiles locales con más de 15 días de inactividad            |
| USER-LOGON | Todos los departamento              | Aplicación en producción de limpieza de perfiles inactivos                   |

  



















  

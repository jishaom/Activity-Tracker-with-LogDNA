---

copyright:
  years: 2019
lastupdated: "2019-05-21"

keywords: IBM Cloud, LogDNA, Activity Tracker, IAM events

subcollection: logdnaat

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Sucesos de IAM
{: #at_events_iam}

Como agente de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.at_full_notm}} para realizar un seguimiento de cómo interactúan los usuarios y las aplicaciones con el servicio {{site.data.keyword.iamlong}} (IAM) en {{site.data.keyword.cloud_notm}}. 
{:shortdesc}

IAM le permite autenticar usuarios de forma segura tanto para servicios de la plataforma como para controlar de forma coherente en el acceso a recursos en {{site.data.keyword.cloud_notm}}. [Más información](/docs/iam?topic=iam-iamoverview).


El servicio {{site.data.keyword.at_full_notm}} registra actividades iniciadas por los usuarios que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para empezar a supervisar las acciones del usuario, consulte [{{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started). Un iniciador puede ser un usuario, un servicio o una aplicación.


## Sucesos de grupos de acceso
{: #at_events_iam_access}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción                      | Descripción |
|-----------------------------|---------|
| `iam-groups.group.create`   | Se genera un suceso cuando un iniciador crea un grupo de acceso. | 
| `iam-groups.group.read`     | Se genera un suceso cuando un iniciador consulta información relacionada con grupos de acceso. |
| `iam-groups.group.update`   | Se genera un suceso cuando un iniciador actualiza un nombre de grupo o una descripción. |
| `iam-groups.group.delete`   | Se genera un suceso cuando un iniciador suprime un grupo de acceso. |
| `iam-groups.member.add`     | Se genera un suceso cuando un iniciador añade un miembro a un grupo de acceso. |
| `iam-groups.member.delete`  | Se genera un suceso cuando un iniciador elimina miembro de un grupo de acceso. |
| `iam-groups.member.read`    | Se genera un suceso cuando un iniciador comprueba la pertenencia de un miembro. |
| `iam-groups.rule.read`      | Se genera un suceso cuando un iniciador visualiza una regla en un grupo de acceso. |
| `iam-groups.rule.create`    | Se genera un suceso cuando un iniciador añade una regla a un grupo de acceso. |
| `iam-groups.rule.update`    | Se genera un suceso cuando un iniciador modifica el nombre de una regla. |
| `iam-groups.rule.delete`    | Se genera un suceso cuando un iniciador suprime una regla de un grupo de acceso. |
{: caption="Tabla 1. Acciones de gestión de grupos de acceso" caption-side="top"} 



## Sucesos de política
{: #at_events_iam_policies}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción                 | Descripción |
|------------------------|---------|
| `iam-am.policy.create` | Se genera un suceso cuando un iniciador añade una política a un usuario o grupo de acceso. |
| `iam-am.policy.delete` | Se genera un suceso cuando un iniciador modifica los permisos sobre una política de un usuario o grupo de acceso.|
| `iam-am.policy.update` | Se genera un suceso cuando un iniciador suprime una política asignada a un usuario o grupo de acceso. |
{: caption="Tabla 5. Acciones de gestión de políticas" caption-side="top"} 



## Sucesos de ID de servicio
{: #at_events_iam_serviceids}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-identity.account-serviceid.create` | Se genera un suceso cuando un iniciador crea un ID de servicio.  | 
| `iam-identity.account-serviceid.update` | Se genera un suceso cuando un iniciador cambia el nombre de un ID de servicio o modifica su descripción. | 
| `iam-identity.account-serviceid.delete` | Se genera un suceso cuando un iniciador suprime un ID de servicio. | 
{: caption="Tabla 2. Acciones de cómo trabajar con ID de servicio" caption-side="top"} 


## Sucesos de clave de API
{: #at_events_iam_apikeys}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción | Descripción |
|----------|---------|
| `iam-identity.user-apikey.create`      | Se genera un suceso cuando un iniciador crea una clave de API. | 
| `iam-identity.user-apikey.update`      | Se genera un suceso cuando un iniciador cambia el nombre de una API o modifica su descripción. |  
| `iam-identity.user-apikey.delete`      | Se genera un suceso cuando un iniciador suprime una clave de API. |  
| `iam-identity.serviceid-apikey.create` | Se genera un suceso cuando un iniciador crea una clave de API para un ID de servicio. |  
| `iam-identity.serviceid-apikey.delete` | Se genera un suceso cuando un iniciador suprime una clave de API para un ID de servicio. |  
{: caption="Tabla 3. Acciones de cómo trabajar con claves de API" caption-side="top"} 


## Sucesos de inicio de sesión
{: #at_events_iam_login}

En la tabla siguiente se muestran las acciones que generan un suceso:

| Acción                                   | Descripción |
|------------------------------------------|---------|
| `iam-identity.user-apikey.login`         | Se genera un suceso cuando un usuario inicia una sesión en {{site.data.keyword.cloud_notm}} utilizando una clave de API. |  
| `iam-identity.serviceid-apikey.login`    | Se genera un suceso cuando un iniciador inicia una sesión en {{site.data.keyword.cloud_notm}} utilizando una clave de API asociada con un ID de servicio. |  
| `iam-identity.user-identitycookie.login` | Este es un suceso que se genera cuando un iniciador solicita una cookie de identidad para ejecutar una acción. |
| `iam-identity.user-refreshtoken.login`   | Este es un suceso que se genera cuando el iniciador inicia una sesión en IBM Cloud, o cuando un iniciador que ya ha iniciado una sesión en IBM Cloud solicita una nueva señal de renovación para ejecutar una acción. |
{: caption="Tabla 4. Acciones de inicio de sesión de usuario" caption-side="top"} 


## Visualización de sucesos
{: #at_events_iam_ui}

Los sucesos están disponibles en la región **Frankfurt (eu-de)**. Para ver estos sucesos, debe [suministrar una instancia](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-provision#provision) del servicio {{site.data.keyword.at_full_notm}} en la región **Frankfurt (eu-de)**. A continuación, debe [abrir la interfaz de usuario de {{site.data.keyword.at_full_notm}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-launch#launch_step2). 


## Análisis de sucesos
{: #at_events_iam_analyze}


### Suprimir un grupo de acceso
{: #an_del_ag}

Al suprimir un grupo de acceso, el suceso que se desencadena tiene un campo `action` establecido en
`iam-groups.group.delete`.

Cuando se suprime un grupo de acceso, tenga en cuenta la información siguiente:
* Se desencadenan automáticamente otras acciones para limpiar otros recursos asociados con el grupo. Algunas acciones que se desencadenan informan sobre sucesos relacionados con la supresión de miembros de un grupo de acceso, la supresión de políticas y la supresión de reglas dinámicas. 
* El iniciador de estas acciones es un ID de servicio de {{site.data.keyword.IBM_notm}}.


Cuando el grupo de acceso que se suprime no tiene miembros, políticas y reglas asignados, los sucesos que se generan para cualquiera de estos recursos informan sobre un resultado de `failure` con un código de resultado de `404`. El ejemplo siguiente muestra los sucesos generados cuando se suprime un grupo de acceso que no tiene miembros, políticas ni reglas dinámicas asignados:

```
Apr 29 14:11:22 IAM Access Groups: delete group test5
Apr 29 14:11:24 IAM Access Groups: delete members -failure
Apr 29 14:11:24 IAM Access Groups: delete rules -failure
Apr 29 14:11:24 IAM Access Management: delete policy -failure
```
{: screen}


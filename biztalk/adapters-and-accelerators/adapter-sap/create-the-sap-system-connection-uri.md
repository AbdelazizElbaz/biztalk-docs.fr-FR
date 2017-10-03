---
title: "Créer l’URI de connexion au système SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI
- how to, connect using connection URI
- connecting using connection URI
- connecting to SAP, using the connection URI
ms.assetid: e41ed488-07a7-4fb7-97c0-6d626e041e95
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f9c224eb7a219cf3e5bb81f31ef8382c555295b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-the-sap-system-connection-uri"></a>Créer l’URI de connexion au système SAP
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] URI de connexion contient des propriétés de l’adaptateur utilise pour établir une connexion au système SAP.  
  
> [!IMPORTANT]
>  Par défaut, la bibliothèque cliente SAP (librfc32u.dll) prend en charge un maximum de 100 connexions au système SAP. Si vous dépassez ce nombre de connexions, une exception est levée. Pour cette raison, vous devez définir le **MaxConnectionsPerSystem** liaison de propriété pour limiter le nombre de connexions qui la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] va tenter d’ouvrir sur le système SAP ; ou définissez la variable d’environnement CPIC_MAX_CONV sur augmenter le nombre de connexions prises en charge par la bibliothèque cliente SAP. Si vous modifiez CPIC_MAX_CONV, vous devez redémarrer votre ordinateur pour que la modification prenne effet. Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 Cette rubrique fournit des informations sur l’URI de connexion SAP et fournit également des liens vers d’autres rubriques qui expliquent comment spécifier un URI de connexion dans différents scénarios de programmation.  
  
## <a name="connection-uri-for-the-sap-adapter"></a>URI de connexion pour l’adaptateur SAP  
 Un type [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] adresse de point de terminaison URI est représenté comme suit :  
  
```  
scheme://userinfoparams@hostinfoparams?query_string  
```  
  
 L’URI d’adresse de point de terminaison contient les composants suivants :  
  
-   schéma est le nom du schéma.  
  
-   userinfoparams est une collection nom-valeur des paramètres requis pour l’authentification utilisateur par le point de terminaison.  
  
-   hostinfoparams est informations requises pour établir la connexion à l’hôte ; par exemple, un chemin d’accès.  
  
-   QUERY_STRING est une collection nom-valeur facultative de paramètres délimités par un point d’interrogation ( ?).  
  
 L’URI d’adresse de point de terminaison qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise pour un système SAP est spécifié à l’aide d’un URI de connexion SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] implémente cette connexion URI comme suit :  
  
```  
sap://user=[USER_NAME];passwd=[PASSWORD];Client=[CLIENT];lang=[LANGUAGE];[UseSnc]=[True|False]@connectiontype/conndetail1/conndetail2?GwHost=[GWHOST]?GwServ=[GWSERV]?MsServ=[MSSERV]?Group=[GROUP]?ListenerDest=[LISTENERDEST]?ListenerGwHost=[LISTENERGWHOST]?ListenerGwServ=[LISTENERGWSERV]?ListenerProgramId=[LISTENERPROGRAMID]?RfcSdkTrace=[true/false]?AbapDebug=[true/false]  
```  
  
 Les composants de l’URI de connexion sont décrits dans les sections suivantes.  
  
### <a name="the-sap-connection-uri-scheme"></a>Le schéma d’URI de connexion SAP  
 Le schéma de l’URI de connexion SAP est « sap ».  
  
### <a name="user-information-in-the-sap-connection-uri"></a>Informations utilisateur dans l’URI de connexion SAP  
 Les informations utilisateur (userinfoparams) dans l’URI est représenté comme une collection nom-valeur des paramètres requis pour l’authentification utilisateur, l’identification de client et spécification du langage de connexion SAP. Le tableau suivant décrit ces paramètres.  
  
|Propriété| Description|  
|--------------|-----------------|  
|Utilisateur|Le nom d’utilisateur sur le système SAP. Cette valeur respecte la casse. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] préserve la casse de la valeur que vous entrez le nom d’utilisateur lorsqu’il ouvre une connexion sur le système SAP.|  
|Mot de passe|Le mot de passe pour l’utilisateur sur le système SAP. Cette valeur respecte la casse. Vous devez définir le **AcceptCredentialsInUri** liaison de propriété **true** pour spécifier le nom d’utilisateur et un mot de passe dans l’URI de connexion. **Remarque :** le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] préserve la casse de la valeur que vous entrez le mot de passe lorsqu’il ouvre une connexion sur le système SAP.|  
|Client|L’id de client du système SAP.|  
|Langage|Langage.|  
|UseSnc|Paramètre facultatif qui spécifie si les Communications de réseau sécurisée (SNC) SAP est activée. La valeur peut être True ou False ; Si la valeur est True, SNC est activé. La valeur par défaut est False<br /><br /> Lorsque vous activez SNC, vous devez également définir le **SncPartnerName** et **SncLibrary** propriétés de liaison. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).<br /><br /> Si SNC est activé et l’URI de connexion contient des informations d’identification, l’adaptateur lève une exception. **Remarque :** UseSnc un paramètre de connexion s’applique uniquement aux types de connexions A et B. Différents types de connexions et leur signification sont décrits en détail plus loin dans cette rubrique.|  
  
> [!NOTE]
>  Vous devez spécifier le Client et la langue dans l’URI de connexion SAP.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces le **AcceptCredentialsinUri** propriété de liaison afin de contrôler si les informations d’identification du système SAP peuvent être spécifiées dans l’URI de connexion. Il s’agit, car les informations d’identification sont représentées sous forme de texte brut dans l’URI de connexion, et ceci pose un risque de sécurité inhérent. Par défaut, le **AcceptCredentialsInUri** liaison de la propriété a la valeur false et l’adaptateur lève une exception si les informations d’identification sont spécifiées dans l’URI de connexion.  
  
 Il existe des scénarios dans lesquels il est nécessaire de spécifier des informations d’identification dans l’URI ; de connexion par exemple, pour recevoir les opérations entrantes à partir de SAP système lorsque vous utilisez WCF service modèle ou le modèle de canal WCF. Vous pouvez définir le **AcceptCredentialsInUri** propriété sur true pour ces scénarios. Il est recommandé, toutefois, pour éviter de fournir des informations d’identification directement dans l’URI de connexion. Pour plus d’informations sur la façon de fournir en toute sécurité les informations d’identification pour la connexion SAP, consultez [sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).  
  
> [!IMPORTANT]
>  Si vous activez les Communications de réseau sécurisée (SNC) en définissant le paramètre UseSnc sur true, l’adaptateur lève une exception.  
  
### <a name="host-information-in-the-sap-connection-uri"></a>Informations sur l’hôte dans l’URI de connexion SAP  
 Les informations d’hôte SAP (hostinfoparams) sont représentées par les éléments suivants dans l’URI de connexion SAP : `connectiontype/conndetail1/conndetail2`. Ces paramètres spécifient les détails sur la connexion cliente au système SAP. Des détails supplémentaires sur la connexion du client SAP, ainsi que des détails qui permettent d’établir une connexion en tant qu’écouteur vers une destination RFC de SAP peuvent être spécifiés dans query_string. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les types suivants de la connexion client dans l’URI de connexion SAP :  
  
-   R : un hôte d’application en fonction de connexion dans laquelle l’URI de connexion spécifie un serveur d’applications par le biais duquel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte à SAP.  
  
-   B : un équilibrage de connexion dans laquelle l’URI de connexion spécifie un serveur de messages par le biais duquel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] se connecte à SAP.  
  
-   D: une connexion basée sur la destination dans lequel l’URI de connexion spécifie une destination dans le fichier saprfc.ini qui contient les paramètres de connexion pour SAP.  

    > [!NOTE]
    > Connexion de Type B s’applique uniquement aux ports d’envoi.  Lorsque vous configurez un emplacement de réception, choisissez un de Type de connexion ou D.
  
 Le tableau suivant décrit la façon dont ces connexions sont spécifiées dans l’URI de connexion SAP.  
  
|Type de connexion|Conndetail1|Conndetail2| Description|  
|---------------------|-----------------|-----------------|-----------------|  
|Un|ASHOST (hôte d’Application serveur)|SYSNR (numéro du système SAP)|Spécifie une connexion basée sur l’hôte d’application. Pour une connexion basée sur l’hôte d’application, un hôte de passerelle et le Service de passerelle facultatif peuvent être spécifié dans query_string.|  
|B|MSHOST (hôte de serveur de Message)|R3NAME (nom de R3 SAP)|Spécifie une connexion via un serveur de messages d’équilibrage de charge. Pour une connexion d’équilibrage de charge, un groupe de serveur facultative et le Message Service peuvent être spécifié dans query_string.|  
|D|CIBLE qui contient les paramètres de connexion dans le fichier saprfc.ini|--|Spécifie une connexion basée sur la destination. Les paramètres de connexion SAP sont contenus dans la destination spécifiée dans le fichier saprfc.ini. Seules les connexions de type et de type B peuvent être spécifiées dans la destination.|  
  
> [!NOTE]
>  Si vous spécifiez des valeurs de connexion dans le fichier saprfc.ini, assurez-vous que le fichier se trouve dans le même dossier que l’accès au fichier .exe ou à un emplacement standard comme requis par le système SAP. Pour plus d’informations, consultez la documentation de SAP.  
  
### <a name="query-information-in-the-sap-connection-uri"></a>Informations de requête dans l’URI de connexion SAP  
 Les informations de requête (query_string) dans l’URI de connexion SAP contient des paramètres facultatifs qui peuvent être inclus pour spécifier les éléments suivants :  
  
-   Détails de connexion supplémentaires pour les connexions d’application basée sur l’hôte (A).  
  
-   Informations de connexion supplémentaires pour chargement les connexions équilibrage (B).  
  
-   Détails de l’écouteur que vous spécifient une Destination RFC sur le système SAP par le biais duquel le système SAP peut envoyer des RFC et IDOC à TRFCs le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Indique si les Communications de réseau sécurisée (SNC) SAP.  
  
-   Informations qui spécifient la configuration de débogage.  
  
 Paramètres de requête sont facultatifs ; Toutefois, les détails de l’écouteur doivent être spécifiés pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] d’agir comme un serveur RFC.  
  
 Le tableau suivant décrit les paramètres de requête et indique les types de connexions SAP pour lesquels ils sont valides.  
  
|Valeur|Type de connexion valide| Description|  
|-----------|---------------------------|-----------------|  
|GwHost|Un|Spécifie le nom d’un hôte de passerelle facultatif dans une connexion basée sur l’hôte d’application.|  
|GwServ|Un|Spécifie le nom d’un service de passerelle facultatif dans une connexion basée sur l’hôte d’application.|  
|MsServ|B|Spécifie le nom d’un service de message facultatif dans une connexion d’équilibrage de charge.|  
|Grouper|B|Spécifie un groupe facultatif de serveurs d’applications dans une connexion d’équilibrage de charge.|  
|ListenerDest|(R)|Spécifie une destination facultatif dans le fichier saprfc.ini dans une connexion au serveur rfc. La destination doit spécifier une connexion de type R.|  
|ListenerGwHost|(R)|Spécifie l’hôte de passerelle pour une connexion au serveur rfc. Ce paramètre est facultatif ; Toutefois, si vous le souhaitez une connexion au serveur rfc et LISTENERDEST n’est pas spécifié ou aucun hôte de passerelle n’est spécifié par la destination du fichier saprfc.ini, LISTENERGWHOST doit contenir un hôte de passerelle valide.|  
|ListenerGwServ|(R)|Spécifie le service de passerelle pour une connexion au serveur rfc. Ce paramètre est facultatif ; Toutefois, si vous le souhaitez une connexion au serveur rfc et LISTENERDEST n’est pas spécifié ou aucun service de passerelle n’est spécifié par la destination du fichier saprfc.ini, LISTENERGWSERV doit contenir un service de passerelle valide.|  
|ListenerProgramId|(R)|Spécifie l’id de programme pour une connexion au serveur rfc. Ce paramètre est facultatif ; Toutefois, si vous le souhaitez une connexion au serveur rfc et LISTENERDEST n’est pas spécifié ou aucun service de passerelle n’est spécifié par la destination du fichier saprfc.ini, LISTENERPROGRAMID doit contenir un service de passerelle valide.|  
|RfcSdkTrace|Tous|Paramètre facultatif qui spécifie si le suivi de RFC bibliothèque est activé. La valeur peut être True ou False ; Si la valeur est True, le suivi de RFC bibliothèque est activé. La valeur par défaut est False.<br /><br /> Le niveau de suivi activé par le paramètre RfcSdkTrace dépend de la variable d’environnement RFC_TRACE.<br /><br /> -Si RFC_TRACE pas présenter ou est définie sur 0, le niveau minimal de suivi est activé.<br />-Vous pouvez définir RFC_TRACE sur 1 ou 2 pour augmenter le niveau de suivi.|  
|AbapDebug|Tous|Paramètre facultatif qui spécifie si ABAP débogage à partir de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] est activé. La valeur peut être True ou False ; Si la valeur est True, le débogage ABAP est activé. La valeur par défaut est False. Si AbapDebug est True, l’interface utilisateur graphique SAP est ouvert.|  
  
 Les paramètres dans la chaîne de requête sont les paramètres SAP et leurs valeurs sont définies par SAP. Pour plus d’informations sur ces paramètres, consultez la documentation SAP.  
  
 L’exemple URI de connexion pour une connexion basée sur l’hôte d’application suivant :  
  
```  
sap://Client=800;lang=EN@A/YourSAPHOST/00  
```  
  
## <a name="connection-uri-properties-in-the-configure-adapter-dialog-box"></a>Propriétés d’URI de connexion dans la boîte de dialogue carte configurer  
 Lorsque vous vous connectez au système SAP avec la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] définir des paramètres d’URI à partir de la connexion le **propriétés de l’URI** onglet dans le **configurer l’adaptateur** boîte de dialogue. Le tableau suivant montre comment les propriétés de l’URI sont affichées dans le **propriétés URI** feuille. (Les propriétés de l’URI sont répertoriées par groupe dans l’ordre de qu'apparition dans la feuille de propriétés de l’URI).  
  
|Catégorie|Propriété URI|Partie URI|  
|--------------|------------------|--------------|  
|Serveur d’applications|Serveur d’application hôte|Conndetail1 (connexion d’informations une type d’hôte)|  
|Serveur d’applications|Hôte de passerelle|GwHost (chaîne de requête)|  
|Serveur d’applications|Service de passerelle|GwServ (chaîne de requête)|  
|Serveur d’applications|Numéro du système|Conndetail2 (connexion d’informations une type d’hôte)|  
|Destination|Nom de destination|Conndetail1 (hôte de type de connexion informations D)|  
|Diagnostics|Trace de la RFC|RfcSdkTrace (chaîne de requête)|  
|Diagnostics|Débogage ABAP|AbapDebug (chaîne de requête)|  
|Informations de connexion|Client|Client (userinfoparams)|  
|Informations de connexion|Langage|Langage (userinfoparams)|  
|Serveur de messages|Nom de groupe serveur d’applications|Groupe (chaîne de requête)|  
|Serveur de messages|Hôte du serveur|Conndetail1 (hôte de type de connexion informations B)|  
|Serveur de messages|Service de serveur de message|MsServ (chaîne de requête)|  
|Serveur de messages|Nom du système r/3|Conndetail2 (hôte de type de connexion informations B)|  
|Divers|Type de connexion|Type de connexion (informations : A, B et D)|  
|Serveur RFC|Nom de destination|ListenerDest (chaîne de requête)|  
|Serveur RFC|Hôte de passerelle|ListenerGwHost (chaîne de requête)|  
|Serveur RFC|Service de passerelle|ListenerGwServ (chaîne de requête)|  
|Serveur RFC|Id de programme|ListenerProgramId (chaîne de requête)|  
|SNC|UseSnc|UseSnc (informations de l’utilisateur)|  
  
## <a name="how-to-specify-a-connection-uri-for-rfc-server-connections"></a>Comment spécifier un URI de connexion pour les connexions au serveur RFC.  
 Pour créer une adresse de point de terminaison via lequel le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut agir comme un serveur RFC, vous devez spécifier un id de programme SAP, un hôte de passerelle SAP et un service de passerelle SAP qui correspondent à une destination RFC sur le système SAP. Pour plus d’informations sur la configuration d’une destination RFC sur SAP, consultez [créer une demande de changement, la destination RFC et envoyer une demande de changement à partir de SAP](creating-an-rfc-in-an-sap-system.md).  
  
 Vous pouvez spécifier l’id de programme, un hôte de passerelle et un service de passerelle dans l’URI de l’une des deux méthodes de connexion :  
  
-   en définissant les paramètres de requête ListenerGwHost, ListenerGwServ et ListenerProgramId  
  
-   en définissant le paramètre de requête ListenerDest vers une destination dans le fichier saprfc.ini qui spécifie une connexion de type R.  
  
> [!NOTE]
>  Si vous spécifiez des valeurs de connexion dans le fichier saprfc.ini, assurez-vous que le fichier se trouve sur le même emplacement que l’accès au fichier .exe ou sur un emplacement standard comme requis par le système SAP. Pour plus d’informations, consultez la documentation de SAP.  
  
 Pour spécifier un URI de connexion pour une connexion au serveur RFC, vous spécifiez une connexion cliente régulières avec une destination RFC spécifiée dans la chaîne de requête, comme dans l’exemple suivant :  
  
```  
sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
```  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise les informations contenues dans la partie userinfoparams et hostinfoparams de l’URI de connexion pour récupérer des métadonnées à partir du système SAP et utilise les informations fournies par les paramètres de l’écouteur dans la chaîne de requête à se pour inscrire en tant qu’un écouteur à la Destination RFC de SAP.  
  
## <a name="using-reserved-characters-in-the-connection-uri"></a>À l’aide de caractères réservés dans l’URI de connexion  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge la spécification d’une URI qui comporte des caractères spéciaux pour une des valeurs de paramètre de connexion. Si les valeurs de paramètre de connexion contiennent des caractères spéciaux, assurez-vous que vous effectuez l’une des opérations suivantes :  
  
-   Si vous spécifiez l’URI dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] à l’aide de [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], vous devez les spécifier en tant que-est dans le **propriétés URI** onglet, autrement dit, sans utiliser de caractères d’échappement. Si vous spécifiez l’URI directement dans le **configurer un URI** champ et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
-   Si vous spécifiez l’URI lors de la création d’un envoi ou port de réception [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration et les paramètres de connexion contiennent des caractères réservés, vous devez spécifier les paramètres de connexion à l’aide de caractères d’échappement corrects.  
  
## <a name="using-the-connection-uri-to-connect-to-the-sap-system"></a>À l’aide de l’URI de connexion pour se connecter au système SAP  
 Pour plus d’informations sur la façon d’établir une connexion au système SAP lorsque vous :  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], consultez [se connecter au système SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
-   Configurer un port d’envoi ou de réception du port (emplacement) dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  
  
-   Utilisez le modèle de canal WCF dans une solution de programmation, consultez [créer un canal à l’aide de SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).  
  
-   Utilisez le modèle de service WCF dans une solution de programmation, consultez [configurer un client de liaison pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).  
  
-   Utilisez WCF Service Model Metadata Utility Tool (svcutil.exe), voir [à l’aide de l’utilitaire de métadonnées ServiceModel avec l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)
---
title: "Adaptateur de Services SharePoint de dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77f88174-118d-4ed6-8449-c89ca195ce5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f9885696df24cd5c5f8321ad3c6dd79d444559a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-sharepoint-services-adapter"></a>Dépannage de l’adaptateur SharePoint Services
Cette rubrique décrit le dépannage de l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS).  
  
## <a name="installation"></a>Installation  
 Lors de l’utilisation de l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] (WSS), deux options s’offrent à vous :  
  
|||  
|-|-|  
|**Utilisez le modèle objet Client** la valeur **Oui**.|**Recommandé**. Lorsque cette option est définie sur Oui, le modèle CSOM (Client-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] est utilisé. L’adaptateur est installé lors de l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Aucune étape d’installation supplémentaire n’est nécessaire. **Remarque :** le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation installe également automatiquement l’objet modèle composant redistribuable SharePoint disponible à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).|  
|**Utilisez le modèle objet Client** la valeur **non**.|**Option déconseillée**. Utilise le modèle SSOM (Service-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> Un service Web est installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], qui peut se trouver sur le même ordinateur que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sur un ordinateur distinct.<br /><br /> Pour installer le service web, exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur et recherchez **adaptateur Windows SharePoint Services**. Consultez [annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) pour les étapes d’installation spécifiques.|  
  
 **Utilisez le modèle objet Client** la valeur **Oui** est recommandé. Lorsque la valeur **Oui**, le service web n’est pas installé sur l’ordinateur SharePoint. Si vous préférez utiliser l’option de service web, vous devez définir **utiliser le modèle objet Client** à **non** sur la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="iis"></a>IIS  
 **Service web BTSharePointAdapterWS.asmx**  
  
 Lorsque l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] est installé sur l’ordinateur SharePoint, le service Web BTSharePointAdapterWS.asmx est créé dans IIS sur l’ordinateur SharePoint. En général, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SharePoint sont installés sur des ordinateurs distincts. Lorsque SharePoint est installé, la base de données SQL de contenu peut être placée en local sur l’ordinateur SharePoint, ou sur un serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distant.  
  
 **Pool d’applications utilise le compte de domaine**  
  
 Lorsque BizTalk et SharePoint sont installés sur des ordinateurs distincts, le pool d’applications IIS exécutant le service Web BTSharePointAdapterWS.asmx doit utiliser un compte de domaine. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les bases de données BizTalk, [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et les bases de données SharePoint [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont tous installés sur le même ordinateur, vous pouvez utiliser un compte local.  
  
 **Scénario double saut**  
  
 Lorsque trois ordinateurs sont impliqués ([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]), ce scénario à double tronçon nécessite l’authentification Kerberos. L’adaptateur SharePoint sur l’ordinateur BizTalk effectue une requête POST vers le service Web BTSharePointAdapterWS.asmx sur l’ordinateur SharePoint. L’ordinateur SharePoint interroge ensuite ses bases de données sur l’ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 Cette requête POST en provenance de l’adaptateur BizTalk doit aboutir. Si vous suspectez une défaillance au niveau de l’authentification, consultez les journaux IIS. Par défaut, les journaux IIS sont dans c:\inetpub\logs\LogFiles\W3SVC*x*. La requête POST doit afficher un code d’état 200 (réussite). Si un code d’état d’échec est retourné, comme une erreur 401.2, suivie d’une erreur 401.1, par un autre 4*xx* des erreurs, puis l’authentification en cas d’échec.  
  
 Lorsque vous utilisez l’authentification Kerberos, des noms de principal de service (SPN) sont requis et la délégation doit être activée.  
  
## <a name="enable-kerberos-authentication"></a>Activation de l’authentification Kerberos  
 Dans un scénario à double tronçon, l’authentification Kerberos et l’activation de la délégation sont requis. Les étapes sont les suivantes :  
  
1.  Activer **Negotiate** sur le serveur IIS/SharePoint. [215383 : comment faire pour configurer IIS pour prendre en charge le protocole Kerberos et le protocole NTLM pour l’authentification réseau](http://support.microsoft.com/kb/215383) répertorie les étapes.  
  
2.  Les noms de principal de service (SPN) sont requis pour les comptes de domaine exécutant le service [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et le pool d’applications sur l’ordinateur IIS/SharePoint. Pour créer un nom de principal de service, utilisez l’outil de ligne de commande SetSPN.exe :  
  
     [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]: [Une mise à jour pour Setspn.exe dans Windows Server 2003 est disponible](http://support.microsoft.com/kb/970536)  
  
     [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]8, [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]: [SetSPN](http://technet.microsoft.com/library/cc731241.aspx)  
  
    > [!IMPORTANT]
    >  La commande SetSPN nécessite des droits d’administrateur de domaine et peut être exécutée à partir de n’importe quel ordinateur dans le domaine.  
  
     Pour renvoyer une liste de tous les noms de principal de service enregistrés dans un compte de domaine :  
  
    ```  
    setspn.exe -l Domain\UserAccount  
    ```  
  
     Création des noms de principal de service :  
  
    1.  Créez un nom de principal de service pour le nom de domaine complet de l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s http/IISSharePointComputerName.domain.com domain\IISApplicationPoolDomainAccount  
        ```  
  
    2.  Créez un nom de principal de service pour le nom NETBIOS de l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s http/IISSharePointComputerNamedomain\IISApplicationPoolDomainAccount  
        ```  
  
    3.  Créez un nom de principal de service pour le nom de domaine complet de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com domain\SQLServerServiceDomainAccount  
        ```  
  
    4.  Créez un nom de principal de service pour le nom de domaine complet et le port TCP de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName.domain.com:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
    5.  Créez un nom de principal de service pour le nom NETBIOS de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerNamedomain\SQLServerServiceDomainAccount  
        ```  
  
    6.  Créez un nom de principal de service pour le nom NETBIOS et le port TCP de l’ordinateur SQL Server utilisé par l’ordinateur IIS/SharePoint :  
  
        ```  
        setspn.exe -s mssqlsvc/SQLComputerName:1433 domain\SQLServerServiceDomainAccount  
        ```  
  
3.  Sur le contrôleur de domaine, accédez à **utilisateurs Active Directory & ordinateurs** et procédez comme suit :  
  
    1.  Vérifiez **n’approuver cet ordinateur pour la délégation à tous les services** pour les ordinateurs suivants :  
  
        -   Serveur SharePoint/IIS  
  
        -   Serveur SQL Server utilisé par SharePoint  
  
    2.  Vérifiez **compte est approuvé pour la délégation** et désactivez **compte est sensible et ne peut pas être délégué** pour les comptes de domaine suivants :  
  
        -   Compte de domaine du service SQL Server  
  
        -   Compte de domaine du pool d’applications IIS  
  
 Pour la résolution des problèmes supplémentaires, accédez à [résolution des problèmes de l’adaptateur Windows SharePoint Services](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer SharePoint Services emplacement de réception](../core/configure-sharepoint-services-receive-location.md)   
 [Configurer le Port d’envoi SharePoint Services](../core/configure-sharepoint-services-send-port.md)   
 [CSOM : L’adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md)
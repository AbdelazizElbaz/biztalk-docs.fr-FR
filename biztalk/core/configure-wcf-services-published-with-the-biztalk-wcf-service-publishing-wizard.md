---
title: "Comment configurer des Services WCF publiés à l’Assistant Publication de services WCF BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services, WCF Service Publishing Wizard
- WCF services, configuring
- configuring, WCF services
- WCF Service Publishing Wizard
ms.assetid: f51b86c0-8c19-453d-a66d-3f373e9f096e
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca265c240f0e20534c5140d0810479152ad90914
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard"></a>Configuration des services WCF publiés à l'aide de l'Assistant Publication de services WCF BizTalk
Après la publication de services WCF avec l'Assistant Publication de services WCF BizTalk, vous devez les configurer correctement. Cette rubrique explique comment configurer les services WCF publiés.  
  
> [!NOTE]
>  Vous devez créer et publier vos projets BizTalk avant d'exécuter l'Assistant Publication de services WCF BizTalk. Pour plus d’informations sur l’utilisation de l’Assistant de publication des services WCF BizTalk, consultez [l’utilisation de l’Assistant de publication de Service WCF de BizTalk pour publier des Orchestrations en tant que Services WCF](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md) et [comment utiliser le Service WCF BizTalk L’Assistant pour publier des schémas en tant que Services WCF publication](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md).  
  
### <a name="to-configure-the-receive-locations-for-a-published-wcf-service"></a>Pour configurer les emplacements de réception pour un service WCF publié  
  
1.  Publiez le projet BizTalk en exécutant l'Assistant Publication de services WCF BizTalk.  
  
2.  Si vous n’avez pas sélectionné la **BizTalk de créer des emplacements de réception** option dans la figure suivante lors de la création du service WCF, créez un port de réception et emplacement de réception pour le service WCF publié, puis sélectionnez l’adaptateur WCF pour le type de transport qui utilise l’emplacement de réception. Vous devez sélectionner le même adaptateur WCF est sélectionné sur la **Type de Service WCF** page affichée dans l’illustration suivante. Pour plus d’informations sur la création d’un emplacement de réception, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
    > [!NOTE]
    >  L'Assistant Publication de services WCF BizTalk crée un fichier de liaison, BindingInfo.xml, dans le dossier \App_Data\Temp du répertoire Web pour le service WCF publié (fichier .svc). Si vous sélectionnez le **les emplacements de réception BizTalk de créer** option, l’Assistant utilise le fichier de liaison pour créer l’emplacement de réception. Dans la console Administration de BizTalk Server, vous pouvez importer ce fichier de liaison pour créer l'emplacement de réception manuellement. Pour plus d’informations sur l’importation d’un fichier de liaison, consultez [l’importation des liaisons](../core/importing-bindings2.md).  
  
     ![Page Type de Service WCF](../core/media/959900fd-44c9-4f3a-8836-9786a2f5e707.gif "959900fd-44c9-4f3a-8836-9786a2f5e707")  
  
3.  Si nécessaire, ouvrez la console Administration de BizTalk Server comme suit : cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur  **Administration de BizTalk Server**.  
  
4.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez l’application où le service WCF généré doit être placée, développez **emplacements de réception**, puis double-cliquez sur l’emplacement de réception pour le service WCF.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **configurer**.  
  
6.  Si l’emplacement de réception héberge l’adaptateur WCF-BasicHttp ou WCF-WSHttp, dans le **propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet, puis configurez les propriétés de sécurité sur l’onglet. Si l’emplacement de réception héberge l’adaptateur WCF-CustomIsolated, dans le **propriétés du Transport** boîte de dialogue, cliquez sur le **liaison** onglet, puis configurez les informations de liaison dans l’onglet.  
  
     ![L’onglet sécurité de WCF &#45; Adaptateur BasicHttp](../core/media/585ecdad-bdee-40c0-b2f1-7ace74d503e5.gif "585ecdad-bdee-40c0-b2f1-7ace74d503e5")  
  
    > [!NOTE]
    >  La propriété Type d'informations d'identification du client du transport pour l'adaptateur WCF isolé doit correspondre au schéma d'authentification du répertoire virtuel Internet Information Services (IIS) hébergeant cet emplacement de réception. Par exemple, si la propriété est définie **Windows**, vous devez également activer **l’authentification Windows intégrée** pour le répertoire virtuel qui héberge cet emplacement de réception. De même, si la propriété est définie sur **Aucun**, vous devez autoriser l'accès anonyme au répertoire virtuel qui héberge cet emplacement de réception. Pour plus d’informations sur la façon de configurer les propriétés de sécurité pour les adaptateurs WCF-BasicHttp et WCF-WSHttp, consultez [comment configurer un emplacement de réception WCF-BasicHttp](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd), et [comment configurer une réception WCF-WSHttp Emplacement](../core/how-to-configure-a-wcf-wshttp-receive-location.md). Pour plus d’informations sur la façon de configurer les informations de liaison, consultez [comment configurer un emplacement de réception WCF-CustomIsolated](../core/how-to-configure-a-wcf-customisolated-receive-location.md).  
  
7.  Si vous n’avez pas sélectionné la **BizTalk de créer des emplacements de réception** option lors de la création des services WCF, dans le **propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet. Sur le **général** onglet, tapez l’URI de cet emplacement de réception le **adresse** zone de texte. Spécifiez le répertoire virtuel ainsi que le nom de fichier .svc que l'Assistant Publication de services WCF BizTalk génère dans la précédente procédure, par exemple : /chemin d'accès/service.svc.  
  
    > [!NOTE]
    >  Le **adresse** propriété doit commencer par une barre oblique (« / ») et se terminer par « .svc ». Le **adresse** propriété ne doit pas contenir un schéma de protocole, le nom d’ordinateur ou le numéro de port tel que http://Host. Seul le chemin d'accès du répertoire virtuel peut être utilisé pour la propriété. Le fichier de balisage du service WCF doit avoir une extension .svc.  
  
     ![L’onglet Général de WCF &#45; Adaptateur BasicHttp](../core/media/1126fa6a-e3e9-44ad-aeb0-90c78226aeeb.gif "1126fa6a-e3e9-44ad-aeb0-90c78226aeeb")  
  
8.  Si vous avez sélectionné **Transport** ou **TransportWithMessageCredential** dans les **mode de sécurité** liste déroulante sur le **sécurité** pour l’onglet les adaptateurs WCF-BasicHttp et WCF-WSHttp, vous devez définir des couche SSL (Secure Sockets) dans IIS. Si vous définissez la **Transport** ou **TransportWithMessageCredential** mode de sécurité dans les informations de liaison pour l’adaptateur WCF-CustomIsolated, vous devez également configurer SSL dans IIS.  
  
9. Si l’emplacement de réception héberge l’adaptateur WCF-BasicHttp ou WCF-WSHttp, dans le **propriétés du Transport** boîte de dialogue zone, configurez le **général**, **liaison**et **Messages** onglets si nécessaire. Si l’emplacement de réception héberge l’adaptateur WCF-CustomIsolated, configurez la **général**, **comportement**, **autres**, et **Messages** onglets fonction de vos besoins. Pour l’adaptateur WCF-CustomIsolated, vous pouvez importer le **adresse (URI)** et **identité du point de terminaison** propriétés sur le **général** onglet, les informations sur le deliaison**Liaison** onglet et les comportements de la **comportement** onglet pour cet emplacement de réception à partir d’un fichier de configuration.  
  
10. Activez l'emplacement de réception pour le service WCF publié à l'aide de la console Administration de BizTalk Server. Pour plus d’informations sur l’activation de l’emplacement de réception, consultez [comment activer un emplacement de réception](../core/how-to-enable-a-receive-location.md).  
  
    > [!NOTE]
    >  Les emplacements de réception sont désactivés lors de leur création. Après avoir créé les emplacements de réception avec l'Assistant Publication de services WCF de BizTalk Server, vous devez les activer.  
  
11. Configurez le pool d'applications IIS pour héberger l'emplacement de réception pour le service WCF publié à l'aide de la console de gestion IIS. Pour plus d’informations sur la façon de configurer le pool d’applications pour les adaptateurs WCF isolés, consultez [de configurer IIS pour les adaptateurs de réception WCF isolés](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).  
  
12. Ouvrez une invite de commandes, accédez au dossier dans lequel l’Assistant Publication de BizTalk Server WCF Service créé le service WCF dans %SystemDrive%\InetPub\\, puis ouvrez le fichier Web.config dans le bloc-notes.  
  
13. Dans le bloc-notes, ajoutez la ligne suivante à l’intérieur de la  **\<system.web >** élément :  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  Ce paramètre est facultatif. Il autorise l'accès de l'application ASP.NET hébergeant le service WCF publié à n'importe quelle ressource exposée à la sécurité du système d'exploitation. Il s'agit du niveau de confiance requis par les services WCF publiés lorsque Windows SharePoint Services est installé et exécuté sur l'ordinateur sur lequel ceux-ci sont hébergés.  
  
14. Dans Internet Explorer, dans le **adresse** zone, tapez l’URL pour le service WCF au format http://*hôte [ : port]*/*apppath* / *nomservicewcf.svc* pour tester le service WCF publié. Ces paramètres sont décrits dans le tableau suivant.  
  
    |Paramètre|Valeur|  
    |---------------|-----------|  
    |*hôte [ : port]*|Nom de l'ordinateur sur lequel vous avez déployé votre service WCF. Le nom du serveur peut être suivi de deux points et du numéro du port.|  
    |*chemin d’application*|Nom du répertoire virtuel et chemin d'accès à l'application Web|  
    |*nomservicewcf.svc*|Nom du fichier .svc du service WCF.|  
  
15. Pour empêcher toute divulgation non intentionnelle de métadonnées de service potentiellement sensibles, il est recommandé de désactiver ce comportement dans un environnement de production en procédant comme suit :  
  
    1.  Dans le bloc-notes, ouvrez le fichier Web.config dans le dossier dans lequel l’Assistant Publication de BizTalk Server WCF Service créé le service WCF dans %SystemDrive%\InetPub\\.  
  
    2.  Dans le bloc-notes, définissez le le **httpGetEnabled** d’attribut dans le  **\<serviceMetadata >** élément à la valeur false, car la ligne suivante :  
  
        ```  
        <serviceMetadata httpGetEnabled="false" httpsGetEnabled="false" />  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF-BasicHttp](http://msdn.microsoft.com/library/5929a338-46e0-4fc4-8837-792d7f7ae0fe)   
 [Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md)   
 [Configuration de l’adaptateur WCF-CustomIsolated](../core/configuring-the-wcf-customisolated-adapter.md)   
 [Comment configurer l’authentification de Site Web IIS dans Windows Server 2003](http://go.microsoft.com/fwlink/?LinkID=75699)
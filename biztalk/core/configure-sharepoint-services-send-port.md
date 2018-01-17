---
title: "Configurer le Port d’envoi SharePoint Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36aadbc2-316f-4e1c-a5a8-b162470acf9e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f424d3ad1b38316802585aefca0a49bf2f67f0a2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-sharepoint-services-send-port"></a>Configuration du port d'envoi SharePoint Services
Cette rubrique compare un port d'envoi statique à un port d'envoi dynamique, et présente également les étapes à suivre afin de créer un port d'envoi [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]. Plus précisément :  
  
 [Port d’envoi statique et le Port d’envoi dynamique](../core/configure-sharepoint-services-send-port.md#BKMK_StaticvsDynamic)  
  
 [Créer un Port d’envoi statique](../core/configure-sharepoint-services-send-port.md#BKMK_StaticSend)  
  
 [Créer un Port d’envoi dynamique](../core/configure-sharepoint-services-send-port.md#BKMK_DynamicSend)  
  
##  <a name="BKMK_StaticvsDynamic"></a>Port d’envoi statique et le Port d’envoi dynamique  
  
||Port d'envoi statique|Port d'envoi dynamique|  
|-|----------------------|-----------------------|  
|Vous devez utiliser un port d'envoi unique avec différents adaptateurs.|non<br /><br /> Lors de la création d'un port d'envoi statique, vous devez indiquer le type de transport.|Oui<br /><br /> En règle générale, un port d'envoi dynamique est ajouté à une orchestration. Le type de transport est configuré dans la logique d'orchestration.|  
|Vous devez utiliser un port d'envoi unique avec différentes propriétés de port d'envoi, telles qu’une URL.|non<br /><br /> Lors de la création d'un port d'envoi statique, vous devez configurer certaines propriétés de l'adaptateur, telles qu’une URL.|Oui<br /><br /> En règle générale, un port d'envoi dynamique est ajouté à une orchestration. Les propriétés sont configurées dans la logique d'orchestration.|  
|Vous devez utiliser le gestionnaire d'envoi par défaut.|non<br /><br /> Le gestionnaire d'envoi peut être configuré lors de la création d'un port d'envoi.|non<br /><br /> Le gestionnaire d'envoi peut être configuré lors de la création d'un port d'envoi.|  
|À utiliser lorsque vous ne savez pas où le message doit être acheminé.|non<br /><br /> Lors de la création d'un port d'envoi statique, vous devez spécifier le type de transport et l'emplacement final.|Oui<br /><br /> L'emplacement final peut être configuré dans une orchestration ou dans un scénario de routage basé sur le contenu. Les règles permettent également de filtrer l'emplacement de destination du message.|  
|Vous devez utiliser un port d'envoi unique pour envoyer des messages à plusieurs partenaires.|non<br /><br /> Lors de la création d'un port d'envoi statique, vous devez spécifier le type de transport et l'emplacement final.|Oui<br /><br /> En règle générale, un port d'envoi dynamique est ajouté à une orchestration. Les propriétés sont configurées dans la logique d'orchestration et sont basées sur des règles que vous spécifiez ; les messages peuvent être envoyés à plusieurs partenaires.|  
  
##  <a name="BKMK_StaticSend"></a>Créer un Port d’envoi statique  
 Lors de la création d'un port d'envoi statique, le port d'envoi fait appel au gestionnaire d'envoi par défaut associé au type de transport. Lorsque vous utilisez la [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] carte, la valeur par défaut est de gestionnaire d’envoi **BizTalkServerApplication**. Pour savoir comment ajouter un nouveau gestionnaire d’envoi, accédez à [comment créer un gestionnaire d’adaptateur](http://go.microsoft.com/fwlink/p/?LinkId=263646).  
  
 Pour créer le port d'envoi statique :  
  
1.  Dans le **Administration de BizTalk Server** de la console, développez **groupe BizTalk [*GroupName*]**, développez **Applications**, puis développez l’application pour contenir le port d’envoi.  
  
2.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
    > [!IMPORTANT]
    >  A **Port d’envoi statique avec sollicitation-réponse** n’est pas configurable avec les [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] carte.  
  
3.  Dans **propriétés**, cliquez sur **Windows SharePoint Services** dans les **Type** liste déroulante. Entrez le **nom**, **Gestionnaire d’envoi**, et **Pipeline d’envoi** propriétés.  
  
4.  Cliquez sur **configurer**. Dans **propriétés**, configurez les éléments suivants :  
  
    |||  
    |-|-|  
    |Port de service Web d'adaptateur|**Requise**. Il s'agit du port configuré sur le site Web IIS hébergeant le service Web de l'adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> Port par défaut est **80**, qui est le port HTTP standard. Si vous utilisez un autre port, vous devez mettre à jour cette valeur.|  
    |Délai d'expiration|**Requise**. Cette valeur, exprimée en millisecondes, détermine le délai d'attente pour que l'adaptateur reçoive une réponse du service Web.<br /><br /> Valeur par défaut est **100 000 ms** (100 secondes).<br /><br /> Augmentez cette valeur si la taille du message ou du lot est supérieure à celle prévue.<br /><br /> Il s'agit du délai d'expiration, en millisecondes, des appels du service Web d'exécution de l'adaptateur adressés au service Web de l'adaptateur Windows SharePoint Services. Vous devrez éventuellement augmenter cette valeur si la taille du message ou du lot est supérieure à la valeur moyenne attendue par l'adaptateur.|  
    |Utiliser le modèle objet client|**Requise**. Détermine si le modèle CSOM (Client-side Server Object Model) ou le modèle SSOM (Service-Side Object Model) SharePoint est utilisé.<br /><br /> Valeur par défaut est **Oui**. La valeur **Oui** à utiliser le CSOM SharePoint sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il n’existe aucune configuration requise sur l'ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> La valeur **non** à utilisent le SSOM SharePoint qui inclut le service web installé sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur.<br /><br /> [Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les composants SSOM et CSOM utilisés par les [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] carte.|  
    |URL Dossier de destination|**Requise**. Il s'agit de l'URL de dossier [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] pour stocker les documents. Entrez le chemin d'accès relatif au site SharePoint, Par exemple, **Documents partagés** ou **Documents partagés/bons Orders /**. Vous pouvez également utiliser une liste comme destination, Par exemple, **listes/tâches**. Si vous spécifiez une liste, le corps du message n’est pas enregistré avec l'élément de liste. Les valeurs extraites du message sont promues dans les colonnes SharePoint. **Remarque :** l’URL de bibliothèque ou un dossier de documents SharePoint peut être différent de son nom. Consultez l'adresse dans le navigateur Web pour connaître l'URL exacte.|  
    |Nom du fichier|**Facultatif**. Entrez le nom du fichier [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> Entrez un nom de fichier, tel que **PurchaseOrder0001.xml** ou une expression. Les expressions incluent toute combinaison de littéraux, de macros et de requêtes XPATH. Par exemple, entrez **PurchOrd-%XPATH=//po:PurchaseOrderId%-%MessageID%.xml**. Si vous n’indiquez aucun nom de fichier, le nom du fichier d'origine, la valeur fournie par l'orchestration ou « Msg-%MessageID%.xml » est utilisé. Consultez [Expressions de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-expressions.md) pour plus d’informations. **Remarque :** lors de l’envoi de messages à une liste, cette valeur de nom de fichier est ignorée et pas enregistrée dans une colonne SharePoint. Vous devez donc mettre à jour la colonne 'Titre' en utilisant l'une des 16 colonnes disponibles. Les listes SharePoint n’ont pas de colonne Nom de fichier.|  
    |Alias d'espaces de noms|**Facultatif**. Il s'agit d'une liste, séparée par des virgules ou des points-virgules, des définitions d'alias d'espaces de noms.<br /><br /> Utilisez ce champ pour définir les alias d'espaces de noms utilisés par les requêtes XPATH introduites dans le champ « Nom de fichier » ou « Valeur de colonne ». Par exemple, entrez **po = 'http://OrderProcess/POrder', conf = 'http://OrderProcess/Confirmation' xmlns = " » ; ipsol = '{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'**. **Remarque :** cette propriété ne remplace pas le WSS. Propriété de contexte de message de ConfigNamespacesAliases définie par l’orchestration. Au lieu de cela, les deux valeurs sont fusionnées.|  
    |Remplacer|**Requise**. S'il existe un fichier, cette option détermine si le fichier est remplacé.<br /><br /> Valeur par défaut est **non**. Les options sont les suivantes :<br /><br /> -   **Ne**: génère une erreur et interrompt le message si un fichier portant le même nom existe.<br />-   **Orchestration**: utilise la valeur définie dans l’orchestration si un fichier portant le même nom existe.<br />-   **Renommer**: renomme le nouveau fichier si un fichier portant le même nom existe.<br />-   **Oui**: remplace un fichier existant s’il a le même nom.<br />     Lorsque la valeur **Oui**, envoyant un grand nombre de messages avec le même nom peut provoquer des erreurs de l’Observateur d’événements SharePoint. Ces erreurs n’ont aucun impact sur l'adaptateur, et un message qui échoue fait l'objet d'une nouvelle tentative d'envoi.|  
    |URL de site SharePoint|**Requise**. Il s'agit de l'URL complète du site Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], Par exemple, http://*SharePointServer*  /sites/TestSite. **Remarque :** un port d’envoi ou emplacement de réception URI ne peut pas dépasser 256 caractères.|  
    |Intégration de Microsoft Office|**Requise**. Pour les messages binaires, vous devez utiliser **non** ou **facultatif**.<br /><br /> Valeur par défaut est **facultatif**. Les options sont les suivantes :<br /><br /> <ul><li>**Ne**: enregistre le document **comme-est**. Vous pouvez utiliser cette option pour les messages binaires.</li><li>**Facultatif**: modifie le document de sorte qu’il s’ouvre automatiquement dans une application Office, comme InfoPath. Si les instructions de traitement sont introuvables, le document est traité **comme-est**. Vous pouvez utiliser cette option pour les messages binaires.</li><li>**Orchestration**: utilise la valeur définie dans l’orchestration.</li><li>**Oui**: modifie le document de sorte qu’il s’ouvre automatiquement dans une application Office, comme InfoPath. Si les instructions de traitement sont introuvables, le message est interrompu.<br /><br />     Lorsque la valeur **Oui**, au moins une des paires propriété suivante est requise :<br /><br /> <ul><li>*Bibliothèque de documents modèles* et *colonne Namespace de modèles*</li><li>*Bibliothèque de modèles de documents de secours* et *colonne Namespace modèles de secours*</li></ul></li><li>**Oui (bibliothèque de formulaires InfoPath)**: si une solution InfoPath réside dans la bibliothèque de formulaires, le document est modifié de sorte qu’il s’ouvre automatiquement dans une application Office, comme InfoPath. Si la bibliothèque de formulaires n’est associée à aucune solution, le message est interrompu.</li></ul>|  
    |Bibliothèque de documents Modèles|**Requis *uniquement* lorsque *modèles Namespace colonne* est rempli**. Il s'agit de la bibliothèque de documents SharePoint qui stocke les solutions InfoPath, Par exemple, **mes Solutions**. L’adaptateur recherche les *bibliothèque de documents modèles* pour une solution InfoPath correspondante. Si aucune solution n’est pas trouvée, l’adaptateur recherche les *bibliothèque de documents modèles de secours*. **Remarque :** le *bibliothèque de documents modèles* requiert au moins une colonne SharePoint de « Une seule ligne de texte » qui est remplie avec les éléments suivants : <ul><li>le nom de l'espace de noms et le nœud racine des documents XML pouvant être ouverts avec la solution InfoPath ;</li><li>OU, le nœud racine du document XML.</li></ul> Pour plus d’informations, consultez [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md).|  
    |Bibliothèque de documents Modèles de secours|**Requis *uniquement* lorsque *colonne modèles de secours Namespace* est rempli**. Il s'agit de la bibliothèque de documents SharePoint qui stocke les solutions InfoPath, Par exemple, **modèles**.<br /><br /> Si aucune solution n’est pas trouvée dans le *bibliothèque de documents modèles*, l’adaptateur recherche *bibliothèque de documents modèles de secours* une solution InfoPath correspondante. Le *bibliothèque de documents modèles de secours* et *bibliothèque de documents modèles* champs peuvent être utilisés avec deux ensembles de solutions InfoPath. Il existe des solutions InfoPath génériques à usage universel et des solutions InfoPath spécialisées qui sont utilisées uniquement pour un partenaire spécifique. Le *bibliothèque de documents modèles de secours* champ doit pointer vers les solutions génériques et le *bibliothèque de documents modèles* doit pointer vers les solutions spécialisées pour ce partenaire spécifique. **Remarque :***bibliothèque de documents modèles de secours* requiert au moins une colonne SharePoint de « Une seule ligne de texte » qui est remplie avec les éléments suivants : <ul><li>le nom de l'espace de noms et le nœud racine des documents XML pouvant être ouverts avec la solution InfoPath ;</li><li>OU, le nœud racine du document XML.</li></ul> Pour plus d’informations, consultez [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md).|  
    |Colonne espaces de noms Modèles de secours|**Requis *uniquement* lorsque *bibliothèque de documents modèles de secours* est rempli**. Il s'agit de la bibliothèque de documents SharePoint qui stocke l'espace de noms des solutions InfoPath, Par exemple, **myNamespace**. **Remarque :** ce champ respecte la casse.|  
    |Colonne d'espace de noms des modèles|**Requis *uniquement* lorsque *bibliothèque de documents modèles* est rempli**. SharePoint *bibliothèque de documents modèles* colonne qui stocke l’espace de noms de la solution InfoPath. Par exemple, **myNamespace**. **Remarque :** ce champ respecte la casse.|  
    |Mot de passe SharePoint Online|**Facultatif**. Il s'agit du mot de passe associé au compte SharePoint Online.|  
    |Nom d'utilisateur SharePoint Online|**Facultatif**. Il s'agit du nom d'utilisateur associé au compte SharePoint Online.|  
    |Colonne `n`|**Facultatif**. La colonne SharePoint qui existe dans le *bibliothèque de documents de Destination*. Mettre à jour cette colonne avec la valeur extraite du message ou spécifiée dans le *valeur de la colonne* champ. **Remarque :** jusqu'à 16 colonnes peut être spécifié. Ce champ respecte la casse.|  
    |Valeur de la colonne `n`|**Facultatif**. Entrez la valeur de colonne à définir pour ce message. Vous pouvez entrer une valeur littérale comme « Bon de commande » ou une expression. Les expressions peuvent se composer d'un mélange de littéraux, macros et requêtes XPATH, Par exemple, entrez **« % XPATH=//po:POAmount% », « %sendingorchestrationid% »**. **Remarque :** jusqu'à 16 colonnes peut être spécifié.|  
  
5.  Cliquez sur **OK** enregistrer les paramètres.  
  
6.  Autres options de configuration du port d'envoi :  
  
    1.  [Configuration des options avancées de transport pour un port d’envoi](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  
  
    2.  [Comment configurer les Options de Transport secondaire pour un Port d’envoi](../core/how-to-configure-backup-transport-options-for-a-send-port.md)  
  
    3.  [Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md)  
  
    4.  [Comment configurer des filtres pour un Port d’envoi](../core/how-to-configure-filters-for-a-send-port.md)  
  
    5.  [Comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md)  
  
    6.  [Comment configurer le suivi d’un Port d’envoi](../core/how-to-configure-tracking-for-a-send-port.md)  
  
##  <a name="BKMK_DynamicSend"></a>Créer un Port d’envoi dynamique  
 Lors de la création d'un port d'envoi dynamique, le gestionnaire d'envoi peut être configuré pour chaque adaptateur. Un port d'envoi dynamique unique peut être utilisé par plusieurs adaptateurs. Consultez [Gestionnaire du Port d’envoi dynamique est Configurable](../core/dynamic-send-port-handler-is-configurable.md) pour connaître les étapes configurer le Gestionnaire de Port d’envoi dynamique.  
  
1.  Dans le **Administration de BizTalk Server** de la console, développez **groupe BizTalk [*GroupName*]**, développez **Applications**, puis développez l’application pour contenir le port d’envoi.  
  
2.  Avec le bouton droit **Ports d’envoi**, cliquez sur **nouveau**, puis choisissez **Port d’envoi unidirectionnel dynamique** ou **Port d’envoi dynamique avec sollicitation-réponse**  
  
3.  Dans **propriétés**, entrez la **nom** et **Pipeline** propriétés  
  
     Cliquez sur **configurer**.  
  
4.  Dans le **configurer le Gestionnaire d’envoi** fenêtre, choisissez le **Gestionnaire d’envoi** pour les adaptateurs individuels. La valeur par défaut est de gestionnaire d’envoi **BizTalkServerApplication**. Pour connaître les étapes ajouter un nouveau gestionnaire d’envoi, accédez à [comment créer un gestionnaire d’adaptateur](http://go.microsoft.com/fwlink/p/?LinkId=263646).  
  
     L'utilisation d'hôtes distincts peut être motivée par plusieurs raisons :  
  
    -   **Exigences 32 bits**: certaines cartes nécessitent un hôte 32 bits, tels que les adaptateurs FTP et POP3. Vous pouvez regrouper tous les adaptateurs ou chaque adaptateur 32 bits dans leur propre hôte.  
  
         [Prise en charge du fonctionnement en 64 bits pour BizTalk Server](../core/biztalk-server-64-bit-support2.md)  
  
    -   **Hôte par fonction**: créer un ordinateur hôte pour l’envoi, un hôte de réception, un ordinateur hôte pour le traitement des orchestrations et un ordinateur hôte pour le suivi.  
  
    -   **Plusieurs paramètres d’hôte**: de nombreux paramètres sont implémentés au niveau de l’hôte. Par conséquent, différents paramètres de limitation peuvent être configurés pour chaque hôte. Par exemple, vous pouvez désactiver la limitation sur HôteA, suivre chaque événement sur HôteB, modifier les paramètres .NET CLR sur HôteC ou augmenter l'utilisation de la mémoire sur HôteD.  
  
    -   **Sécurité**: sécurité est implémentée au niveau de l’hôte. Chaque hôte est exécuté sous son propre compte Windows. Par exemple, HôteA utilise l'adaptateur FILE pour accéder à un partage de fichiers. Octroyez les autorisations d'accès au partage de fichiers au compte d'utilisateur HôteA. HôteB utilise un service Web hébergé sur un serveur IIS. Octroyez les autorisations d'accès au service Web au compte d'utilisateur HôteB. Cela empêche également d'autres comptes d'hôtes d'accéder à des entités auxquelles ils n’ont pas besoin d'accéder.  
  
    -   **Des cartes distinctes**: par exemple, vous disposez de plusieurs artefacts (emplacement de réception et ports d’envoi) à l’aide de l’adaptateur HTTP. Vous souhaitez que tous les éléments associés à l'adaptateur HTTP se trouvent dans leur propre hôte.  
  
    -   **Orchestrations distinctes**: orchestrations individuelles peuvent se trouver dans leur propre hôte. Par exemple, si une orchestration utilise la mémoire ou le processeur de manière intensive, placez cette orchestration dans son propre hôte.  
  
     [Le Guide de l’optimisation de performances de BizTalk Server](http://msdn.microsoft.com/library/dn775063\(v=bts.10\).aspx) et [comment gérer et dépanner les bases de données BizTalk Server](http://support.microsoft.com/kb/952555) fournissent des suggestions de performances.  
  
5.  Cliquez sur **OK** enregistrer les paramètres.  
  
6.  Autres options de configuration du port d'envoi :  
  
    1.  [Configuration des options avancées de transport pour un port d’envoi](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  
  
    2.  [Comment configurer les mappages sortants pour un Port d’envoi](../core/how-to-configure-outbound-maps-for-a-send-port.md)  
  
    3.  [Comment configurer des filtres pour un Port d’envoi](../core/how-to-configure-filters-for-a-send-port.md)  
  
    4.  [Comment attribuer un certificat à un Port d’envoi](../core/how-to-assign-a-certificate-to-a-send-port.md)  
  
    5.  [Comment configurer le suivi d’un Port d’envoi](../core/how-to-configure-tracking-for-a-send-port.md)  
  
7.  Cliquez sur **OK** enregistrer les paramètres.  
  
 Autres rubriques relatives aux ports d'envoi :  
  
 [Création et configuration des ports d’envoi](../core/creating-and-configuring-send-ports.md)  
  
 [Création et configuration des groupes de ports d’envoi](../core/creating-and-configuring-send-port-groups.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de l’adaptateur SharePoint Services](../core/troubleshooting-sharepoint-services-adapter.md)   
 [Configurer SharePoint Services emplacement de réception](../core/configure-sharepoint-services-receive-location.md)   
 [Modèle CSOM : Adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md)
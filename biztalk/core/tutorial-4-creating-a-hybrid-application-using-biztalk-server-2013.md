---
title: "Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a9de95f-7d2c-437d-be5b-0062592f32c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c11b163f34a1320052de585c7ddfc79afb03db4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013"></a>Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013
Cette section contient une procédure pas à pas pour la création d'une application hybride impliquant [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="business-scenario"></a>Scénario d'entreprise  
 Northwind est une entreprise qui reçoit des commandes client en provenance de ses partenaires, dont l'un d'eux est Contoso, sous la forme de messages EDI de type fichier plat. Northwind souhaite configurer une application de bout en bout pour les tâches suivantes :  
  
-   **Gérer le traitement des messages EDI** : ce module de l’application doit vérifier que le message reçu à partir de Contoso est conforme aux formats de message EDI standards. Ce module doit également générer tous les accusés de réception nécessaires pour vérifier que le message a été correctement traité.  
  
-   **Utiliser la logique métier pour traiter les données** – une fois le message EDI est correctement vérifié et traité, Northwind doit exécuter le message par rapport à la logique métier pour un traitement ultérieur. Par exemple, si la quantité commandée figurant dans le message reçu est supérieure à une quantité donnée, les données sont stockées dans une base de données SQL Server. Sinon, les données sont envoyées dans un emplacement de fichier partagé.  
  
 Pour mettre en œuvre ce scénario, Northwind décide de configurer une application hybride dans laquelle le traitement des messages EDI est effectué dans le cloud, et le traitement des données pilotées par la logique métier est effectué en local. Pour configurer cette application hybride, Northwind utilise les ressources suivantes :  
  
-   **[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]**– Le portail Azure BizTalk disponible avec [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] permet aux clients de configurer des partenaires commerciaux et des accords EDI sur [!INCLUDE[winazure](../includes/winazure-md.md)]. Northwind utilise la version de [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] d'avril 2012 pour créer et déployer un accord servant à traiter le message EDI entrant, à le valider par rapport au schéma de commande client X12 840, à le transformer selon un schéma requis par Northwind, puis à l'envoyer vers une file d'attente Service Bus. En résumé, pour développer une application hybride, les données doivent être envoyées de la file d'attente Service Bus vers une application locale.  
  
-   **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**: Le nouvel adaptateur pour Service Bus (**SB-Messaging**) disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux applications de recevoir des messages à partir des entités Service Bus, comme les files d’attente, rubriques, et ainsi de suite dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans le cadre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, Northwind utilise une orchestration pour décider si la quantité demandée de la commande reçue est supérieure à 100. Si la quantité est supérieure à 100, le message est inséré dans une table de base de données SQL Server appelée **SalesOrder**. Si la quantité est inférieure à 100, le message est envoyé dans un emplacement de fichier partagé.  
  
     Pour insérer le message dans une table de base de données SQL Server, Northwind utilise l'[!INCLUDE[adaptersql](../includes/adaptersql-md.md)] disponible dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
### <a name="end-to-end-message-flow"></a>Flux de messages de bout en bout  
 Voici le trajet du message dans l'application hybride :  
  
1.  Contoso envoie un message de commande client X12 vers le point de terminaison où est déployé l'accord EDI dans le cloud.  
  
2.  Une fois que le message a été correctement traité via l'accord EDI, il est envoyé vers la file d'attente Service Bus.  
  
3.  L'adaptateur de réception SB-Messaging consomme le message en provenance de la file d'attente Service Bus et instancie l'orchestration déployée dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de manière à envoyer le message vers différentes destinations, en fonction de la quantité commandée.  
  
4.  Si la quantité commandée est supérieure à 100, l’orchestration insère le message à un **SalesOrder** table. En revanche, si la quantité commandée est inférieure ou égale à 100, le message est écrit dans un emplacement de fichier partagé.  
  
## <a name="set-up-your-computer"></a>Configuration de votre ordinateur  
 Ce didacticiel nécessite que vous réalisiez quatre activités à caractère général. Le tableau suivant répertorie les activités ainsi que la configuration logicielle requise pour chaque activité :  
  
|Activité|Logiciels requis|  
|--------------|-----------------------|  
|Création des artefacts EDI nécessaires à l'accord EDI|Ce didacticiel a été créé avec la version de [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] d'avril 2012 ainsi qu’avec le schéma de commande client X12 840. Ils peuvent être téléchargés à partir de [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).|  
|Création et déploiement de l'accord EDI|Étant donné que l'accord EDI est déployé sur Azure, vous avez uniquement besoin d'un navigateur Web (par exemple, Internet Explorer) pour vous connecter au Portail Azure BizTalk.|  
|Création, déploiement et configuration de l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|Si vous voulez configurer un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur sur une machine virtuelle Azure, suivez les instructions à [http://msdn.microsoft.com/library/azure/jj248689.aspx](http://msdn.microsoft.com/library/azure/jj248689.aspx).|  
|Envoi d'un message de test au point de terminaison de l'accord EDI|Vous pouvez utiliser l'outil MessageSender disponible dans le package d'exemples fourni avec [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]. Vous pouvez télécharger le package d’exemples [http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057).|  
  
 Vous pouvez choisir d'installer tous ces éléments sur un même ordinateur, ou sur des ordinateurs distincts.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 (pour Azure) : Créer le projet EDI](../core/step-1-for-azure-create-the-edi-project.md)  
  
-   [Étape 2 (pour Azure) : Créer un accord EDI](../core/step-2-for-azure-create-an-edi-agreement.md)  
  
-   [Étape 3 (pour Azure) : Créer une file d’attente du Bus de Service](../core/step-3-for-azure-create-a-service-bus-queue.md)  
  
-   [Étape 4 (sur site) : Créer la Table SQL Server](../core/step-4-on-premises-create-the-sql-server-table.md)  
  
-   [Étape 5 (locaux) : Générer le schéma pour l’insertion d’un Message dans la SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)  
  
-   [Étape 6 (sur site) : Créer une transformation pour mapper le Message à partir de la file d’attente vers le schéma Insert](../core/step-6-map-the-message-from-the-queue-to-the-insert-schema.md)  
  
-   [Étape 7 (en local) : Création d’une Orchestration](../core/step-7-on-premises-create-an-orchestration.md)  
  
-   [Étape 8 (en local) : Configurer l’Application BizTalk Server](../core/step-8-on-premises-configure-the-biztalk-server-application.md)  
  
-   [Étape 9 : Tester la Solution](../core/step-9-test-the-solution.md)
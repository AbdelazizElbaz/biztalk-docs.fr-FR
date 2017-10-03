---
title: "À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, compatibility
ms.assetid: 278a13ff-8e46-4af4-a76e-b6d4aad5b768
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba635b9bc4569f17418fc925c54c64d0fdc67461
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a>À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur
Sous Windows, les versions [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)], [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] de l'adaptateur MQSeries sont toutes compatibles avec le même serveur distant WebSphere MQ. Ceci est dû au fait que les versions suivantes des applications COM+ utilisées par l'adaptateur MQSeries peuvent coexister sur le même ordinateur MQSeries WebSphere :  
  
-   **L’application MQSAgent (MQSAgent2) COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)].  
  
-   **Application MQSAgent COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)].  
  
-   **Application MQHelper COM +** utilisé avec l’adaptateur MQSeries pour [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)].  
  
> [!NOTE]
>  Lors de la configuration d'une installation côte à côte de ces applications COM+, assurez-vous qu'aucune d'entre elles ne soit configurée de manière à utiliser les mêmes files d'attente MQSeries.  
  
> [!IMPORTANT]
>  Une installation côte à côte de la version [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] de l'application COM+ de l'adaptateur MQSeries avec une version antérieure est uniquement prise en charge si une version antérieure de BizTalk Server n'est pas installée sur l'ordinateur MQSeries WebSphere.  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a>Pour installer la version BizTalk Server 2006 de l'application COM+ de l'adaptateur MQSeries sur un ordinateur MQSeries WebSphere exécutant une version antérieure de cette application  
  
1.  Exécutez le fichier Bootstrap.msi se trouvant dans le répertoire \Platform\BootStrap\ du CD [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] afin de copier les fichiers de dépendances MSVCR80.dll et MSVCP80.dll sur l'ordinateur MQSeries WebSphere.  
  
2.  Copiez le fichier MQSAgent.dll situé dans le répertoire \Msi\Program Files\ du CD [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] sur l'ordinateur MQSeries WebSphere.  
  
    > [!NOTE]
    >  Si vous envisagez d'utiliser l'utilitaire de suivi MQSAgent, copiez également le fichier MQSTrace.cmd situé dans le même répertoire vers l'ordinateur MQSeries WebSphere. Pour plus d’informations sur l’application MQSAgent utilitaire de suivi consultez [analyse des erreurs de l’adaptateur MQSeries avec les outils de suivi](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md).  
  
3.  Enregistrez manuellement les composants dans le fichier MQSAgent.dll en exécutant la commande regsvr32 mqsagent.dll sur l'ordinateur MQSeries WebSphere :  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  Exécutez cette commande à partir du répertoire dans lequel vous avez copié le fichier MQSAgent.dll.  
  
4.  Créez une application COM+ pour les composants MQSAgent :  
  
    -   Cliquez sur Applications COM +, cliquez sur **nouveau**, **Application** pour afficher la **Assistant Installation d’applications COM +** et cliquez sur **suivant**.  
  
    -   Cliquez sur **créer une application vide**.  
  
    -   Entrez le nom **MQSAgent2**, laissez l’option par défaut **application serveur** activé, puis cliquez **suivant**.  
  
    -   Sélectionnez l’option de **cet utilisateur**, entrez les informations de compte approprié, puis cliquez sur **suivant**.  
  
        > [!NOTE]
        >  Ce compte doit avoir reçu les autorisations de connexion, de placement et/ou d'obtention pour les files d'attente IBM WebSphere MQ appropriées.  
  
    -   Cliquez sur **suivant** sur l’ajout de **les rôles d’Application** boîte de dialogue.  
  
    -   Cliquez sur **suivant** sur la **ajouter des utilisateurs aux rôles** boîte de dialogue.  
  
    -   Cliquez sur **Terminer**.  
  
5.  Ajoutez les composants MQSAgent.dll à l'application MQSAgent2 COM+ :  
  
    -   Cliquez pour développer le **MQSAgent2** l’Application COM +.  
  
    -   Avec le bouton droit **composants** et cliquez sur **nouveau**, **composant** pour lancer l’Assistant Installation du composant COM +, puis cliquez sur **suivant**.  
  
    -   Cliquez sur **installer de nouveaux composants**, recherchez le fichier MQSAgent.dll, puis sur **ouvrir**.  
  
    -   Cliquez sur **Suivant**, puis sur **Terminer**.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)
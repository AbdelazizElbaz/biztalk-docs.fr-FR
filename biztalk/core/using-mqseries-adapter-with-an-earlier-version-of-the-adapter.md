---
redirect_url: /biztalk/core/mqseries-adapter-deployment-options
redirect_document_id: 
ROBOTS: NOINDEX
ms.openlocfilehash: 2aa74be2d86bcb8f32661fdcf06727eb6391861d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a>À l’aide de l’adaptateur MQSeries avec une Version antérieure de l’adaptateur
Les différentes versions de BizTalk Server de l’adaptateur MQSeries peuvent fonctionner avec le même serveur distant WebSphere MQ sur Windows. Ceci est dû au fait que les versions suivantes des applications COM+ utilisées par l'adaptateur MQSeries peuvent coexister sur le même ordinateur MQSeries WebSphere :  
  
-   **L’application MQSAgent (MQSAgent2) COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2006) 
  
-   **Application MQSAgent COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2004)  
  
-   **Application MQHelper COM +** utilisé avec l’adaptateur MQSeries (BizTalk Server 2002) 
  
> [!NOTE]
>  Lors de la configuration d'une installation côte à côte de ces applications COM+, assurez-vous qu'aucune d'entre elles ne soit configurée de manière à utiliser les mêmes files d'attente MQSeries.  
  
> [!IMPORTANT]
>  Installation côte à côte de la version de BizTalk Server 2006 de l’application COM + adaptateur MQSeries avec une version antérieure de l’application COM + MQSeries Adapter n’est possible que si une version antérieure de BizTalk Server n’est pas installée sur le WebSphere Ordinateur MQSeries.  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a>Pour installer la version BizTalk Server 2006 de l'application COM+ de l'adaptateur MQSeries sur un ordinateur MQSeries WebSphere exécutant une version antérieure de cette application  
  
1.  Exécutez le bootstrap.msi dans le répertoire \Platform\BootStrap\ du CD BizTalk Server 2006 pour copier les fichiers de dépendances MSVCR80.dll et MSVCP80.dll sur l’ordinateur WebSphere MQSeries.  
  
2.  Copiez le fichier MQSAgent.dll à partir du répertoire \Msi\Program Files\ sur le CD-ROM de BizTalk Server 2006 à l’ordinateur WebSphere MQSeries.  
  
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
 [Utilisation de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)
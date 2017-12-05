---
title: "Comment configurer une Application de Workflow Foundation pour l’Interception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c82e83f-9dbd-4325-9f30-778eba892296
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70afa4ffae47abf5cdd541846831b4054414eff8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-a-workflow-foundation-application-for-interception"></a>Configuration d'une application Foundation pour l'interception
Avant de commencer à collecter les données d'activité BAM, vous devez installer le logiciel de l'intercepteur [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] et configurer votre application afin d'utiliser le service de l'intercepteur BAM. Vous devez avoir correctement installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ses dépendances et avoir créé au moins un groupe BizTalk.  
  
## <a name="installing-the-bam-eventing-software"></a>Installation du logiciel BAM-Événements  
 Avant de configurer votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] afin d'utiliser l'intercepteur BAM pour [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur l’installation du logiciel BAM-événements et l’enregistrement des compteurs de performance, consultez [l’installation du logiciel BAM-événements](../core/installing-the-bam-eventing-software.md).  
  
## <a name="configuring-a-windows-workflow-foundation-application-for-tracking"></a>Configuration d'une application Windows Workflow Foundation pour le suivi  
 Vous devez effectuer quatre tâches avant que votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] ne puisse commencer à écrire des informations sur les événements BAM :  
  
-   Vous devez créer un modèle d'observation à l'aide des outils BAM de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis le déployer à l'aide de l'outil de ligne de commande du gestionnaire BAM (bm.exe).  
  
-   Un fichier de configuration de l’intercepteur doit être créé et déployé à l’aide de l’outil en ligne de commande Gestionnaire BAM (bm.exe).  
  
-   L’utilisateur qui exécute l’application hôte doit être un membre de l’enregistreur d’événements d’activité BAM approprié (bam_\<activité\>_EventWriter) les rôles SQL Server pour autoriser l’application à lire des informations de configuration de l’intercepteur et d’écriture pour les activités BAM.  
  
-   Vous devez modifier le fichier App.config ou l'application pour charger le service de suivi BAM, puis redémarrer l'application.  
  
 Ce n'est qu'une fois que vous aurez effectué ces tâches correctement que les événements commenceront à apparaître dans la base de données BAM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="deploying-an-observation-model"></a>Déploiement d'un modèle d'observation  
 Vous devez avoir préalablement déployé un modèle d'observation avant de déployer un fichier de configuration d'intercepteur ou de capturer des activités BAM dans votre application.  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a>Pour déployer un modèle d'observation à l'aide de bm.exe  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.  
  
2.  Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.  
  
3.  Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le modèle d'observation à déployer. Par exemple, **cd c:\businessprocess\Orders**.  
  
4.  Déployez le modèle d'observation à l'aide de bm.exe :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe déployer-all - definitionfile :\<*definitionfile.xml*\>  
  
     Veillez à remplacer \< *definitionfile.xml* \> avec le nom du fichier d’observation à déployer. Pour plus d’options, consultez [les commandes de gestion de l’intercepteur](../core/interceptor-management-commands.md).  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.  
  
### <a name="deploying-an-interceptor-configuration-file"></a>Déploiement d'un fichier de configuration d'intercepteur  
 Vous devez déployer un fichier de configuration de l’intercepteur avant que votre application peut capturer des activités BAM.  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a>Pour déployer un fichier de configuration d'intercepteur à l'aide de bm.exe  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.  
  
2.  Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.  
  
3.  Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le fichier de configuration d'intercepteur à déployer. Par exemple, **cd c:\businessprocess\Orders**.  
  
4.  Déployez le fichier de configuration d'intercepteur à l'aide de bm.exe :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe déployer-intercepteur - filename :\<*icfile.xml*\>  
  
     Veillez à remplacer \< *icfile.xml* \> avec le nom du fichier de configuration de l’intercepteur à déployer.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la **-Force : True** indicateur pour remplacer les sources d’événements existantes avec le même nom que ceux figurant dans votre fichier de configuration de l’intercepteur. Si vous le faites, assurez-vous que vous sauvegardez la configuration existante à l’aide de la **get-interceptor** commande. L'utilisation de l'indicateur -Force:True pourrait supprimer des configurations d'intercepteur qui font référence aux sources d'événements remplacées.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Type **Exit**, puis appuyez sur ENTRÉE pour fermer l’invite de commandes.  
  
 Si vous avez déjà déployé votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], la nouvelle configuration ne sera chargée qu'au prochain intervalle d'interrogation. Toutefois, si vous configurez et redémarrez votre application, la configuration est immédiatement récupérée.  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a>Ajout de l'utilisateur au rôle approprié de l'activité BAM  
 L'infrastructure de l'intercepteur BAM utilise les rôles SQL Server par activité pour contrôler l'accès aux activités et aux informations de configuration. Vous devez ajouter le compte d'utilisateur exécutant votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] au(x) rôle(s) approprié(s) de l'activité BAM dans la base de données d'importation principale BAM.  
  
### <a name="configuring-the-application-to-load-the-bam-tracking-service"></a>Configuration de l'application pour charger le service de suivi BAM  
 Il existe trois scénarios de chargement du service de suivi BAM dans votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] :  
  
-   Si votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] utilise déjà la classe WorkflowRuntime pour charger une section de configuration [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous pouvez ajouter les informations du service de suivi BAM à la section existante.  
  
-   Si votre application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] n'utilise pas la classe WorkflowRuntime pour charger une section de configuration [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], vous devez ajouter du code pour charger une section personnalisée de votre fichier de configuration d'application. Vous devez créer la section et lui ajouter les informations du service de suivi BAM.  
  
-   Si vous préférez coder la configuration en dur, vous pouvez utiliser l'API [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] pour charger le service de suivi par programme sans fichier de configuration ou charger la configuration depuis une source personnalisée.  
  
 Lorsque vous configurez l'application [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)], notez les points suivants :  
  
-   L'intercepteur [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] ne prend en charge qu'une instance BamTrackingService par instance WorkflowRuntime.  
  
-   L'intercepteur [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] prend en charge plusieurs instances BamTrackingService par domaine d'application.  
  
    -   Un nombre N d'instances BamTrackingService est pris en charge pour un nombre N d'instances WorkflowRuntime.  
  
-   L'intercepteur génère une exception si des chaînes de connexion différentes sont utilisées pour séparer les instances BamTrackingService dans le même domaine d'application.  
  
-   L'intercepteur obtient la valeur d'intervalle d'interrogation de la configuration d'intercepteur auprès de la première instance BamTrackingService qui démarre.  
  
-   L'intercepteur arrête le thread d'interrogation de la configuration d'intercepteur lorsque la dernière instance BamTrackingService dans le domaine d'application est arrêtée.  
  
 Pour plus d’informations sur la classe WorkflowRuntime et le chargement des informations de configuration, consultez [http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314).  
  
##### <a name="to-configure-the-appconfig-file-for-the-bam-tracking-service"></a>Pour configurer le fichier App.config pour le service de suivi BAM  
  
1.  Ouvrez le fichier App.config associé à votre application. Vous pouvez utiliser Notepad.exe ou un autre éditeur de texte pour cette tâche.  
  
2.  Ajoutez le service de suivi BAM en insérant les informations de configuration suivantes dans le fichier App.config. Il doit être positionné de sorte à être un enfant de l'élément `configuration`.  
  
    > [!NOTE]
    >  L'élément de section doit correspondre au nom utilisé par votre code d'application lors de l'utilisation de la classe WorkflowRuntime.  
  
    ```  
    <!-- The element name must match the one expected by WorkflowRuntime in your WF application -->  
    <WorkflowServiceContainer>  
      <Services>  
        <add type="Microsoft.BizTalk.Bam.Interceptors.Workflow.BamTrackingService, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
       ConnectionString="Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"   
          PollingIntervalSec="5"/>  
        </Services>  
    </WorkflowServiceContainer>  
    ```  
  
3.  Modifier la **ConnectionString** attribut pour correspondre à votre environnement.  
  
4.  Redémarrez votre application.  
  
##### <a name="to-modify-your-application-to-load-a-custom-configuration-section"></a>Pour modifier votre application afin de charger une section de configuration personnalisée  
  
1.  Ouvrez votre projet Windows Workflow Foundation dans Visual Studio.  
  
2.  Ajoutez une nouvelle instance BamTrackingService avec les paramètres appropriés à l'instance de la classe WorkflowRuntime de l'application :  
  
    ```  
    // !! Replace "WorkflowServiceContainer" with the section name  
    // you used in your App.config file.  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime("WorkflowServiceContainer");  
    ```  
  
3.  Recompilez et déployez l'application modifiée.  
  
##### <a name="to-modify-your-application-to-programmatically-load-the-bam-tracking-service"></a>Pour modifier votre application afin de charger par programme le service de suivi BAM  
  
1.  Ouvrez votre projet Windows Workflow Foundation dans Visual Studio.  
  
2.  Ajoutez une nouvelle instance BamTrackingService avec les paramètres appropriés à l'instance de la classe WorkflowRuntime de l'application :  
  
    ```  
    string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"  
    int pollingInterval = 5;  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
    workflowRuntime.AddService(new BamTrackingService(connectionString, pollingInterval));  
    ```  
  
     Vous pouvez ajouter ou supprimer des paramètres en fonction de votre environnement spécifique.  
  
3.  Recompilez et déployez l'application modifiée.
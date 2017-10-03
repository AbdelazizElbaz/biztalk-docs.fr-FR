---
title: "Comment configurer une Application Windows Communication Foundation pour l’Interception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37f2ccde-aa79-470a-ac31-57e4168dc54a
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 103eb58223ba4acd61d909640bacda76d08efe8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-windows-communication-foundation-application-for-interception"></a>Configuration d'une application Windows Communication Foundation pour l'interception
Avant de commencer à collecter les données d'activité BAM, vous devez installer le logiciel de l'intercepteur BAM et configurer votre application afin d'utiliser le service de l'intercepteur BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]. Vous devez avoir correctement installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et ses dépendances et avoir créé au moins un groupe BizTalk.  
  
## <a name="installing-the-bam-eventing-software"></a>Installation du logiciel BAM-Événements  
 Avant de configurer votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] afin d'utiliser l'intercepteur BAM pour [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], vous devez installer le logiciel BAM-Événements à l'aide du programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur l’installation du logiciel BAM-événements et l’enregistrement des compteurs de performance, consultez [l’installation du logiciel BAM-événements](../core/installing-the-bam-eventing-software.md).  
  
## <a name="configuring-a-wcf-application-for-tracking"></a>Configuration d'une application WCF pour le suivi  
 Vous devez effectuer quatre tâches avant que votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] ne puisse commencer à écrire des informations sur les événements BAM :  
  
-   Un modèle d’observation doit être créé à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM des outils et puis déployé à l’aide de l’outil de ligne de commande du gestionnaire BAM (bm.exe).  
  
-   Vous devez créer un fichier de configuration d'intercepteur et le déployer à l'aide de l'outil de ligne de commande du gestionnaire BAM (bm.exe).  
  
-   L’utilisateur qui exécute l’application hôte doit être un membre de l’enregistreur d’événements d’activité BAM approprié (bam_\<activité > _EventWriter) les rôles SQL Server pour permettre à l’application lire des informations de configuration de l’intercepteur et écrire dans l’analyse BAM activités.  
  
-   Vous devez modifier le fichier App.config pour le serveur et l'application cliente pour charger le service de suivi BAM. Une fois le fichier App.config modifié, vous devez redémarrer l'application.  
  
 Ce n'est qu'une fois que vous aurez effectué ces tâches correctement que les événements commenceront à apparaître dans la base de données BAM [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="deploying-an-observation-model"></a>Déploiement d'un modèle d'observation  
 Vous devez avoir préalablement déployé un modèle d'observation avant de déployer un fichier de configuration d'intercepteur ou de capturer des activités BAM dans votre application.  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a>Pour déployer un modèle d'observation à l'aide de bm.exe  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.  
  
2.  Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.  
  
3.  Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le modèle d'observation à déployer. Par exemple, **cd c:\businessprocess\Orders**.  
  
4.  Déployer le modèle d’observation à l’aide de bm.exe :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe déployer-all - Definitionfile :\<*definitionfile.xml*>  
  
     Veillez à remplacer \< *definitionfile.xml*> avec le nom du fichier de modèle d’observation à déployer. Pour plus d’options, consultez [les commandes de gestion de l’intercepteur](../core/interceptor-management-commands.md).  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Type **Exit** et appuyez sur ENTRÉE pour fermer l’invite de commandes.  
  
### <a name="deploying-an-interceptor-configuration-file"></a>Déploiement d'un fichier de configuration d'intercepteur  
 Vous devez déployer un fichier de configuration d'intercepteur pour que votre application puisse capturer des activités BAM.  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a>Pour déployer un fichier de configuration d'intercepteur à l'aide de bm.exe  
  
1.  Cliquez sur **Démarrer** puis cliquez sur **exécuter** pour ouvrir l’invite de commandes Windows.  
  
2.  Type **cmd** dans les **ouvrir** champ, puis cliquez sur **OK**.  
  
3.  Utilisez la commande cd (changer de répertoire) pour accéder au répertoire contenant le fichier de configuration d'intercepteur à déployer. Par exemple, **cd c:\businessprocess\Orders**.  
  
4.  Déployez le fichier de configuration d'intercepteur à l'aide de bm.exe :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe déployer-intercepteur - Filename :\<*icfile.xml*>  
  
     Veillez à remplacer \< *icfile.xml*> par le nom du fichier de configuration de l’intercepteur à déployer.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la **-Force : True** indicateur pour remplacer les sources d’événements existantes avec le même nom que ceux figurant dans votre fichier de configuration de l’intercepteur. Si vous le faites, assurez-vous que vous sauvegardez la configuration existante à l’aide de la **get-interceptor** commande. L'utilisation de l'indicateur -Force:True pourrait supprimer des configurations d'intercepteur qui font référence aux sources d'événements remplacées.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Type **Exit** et appuyez sur ENTRÉE pour fermer l’invite de commandes.  
  
 Si vous avez déjà déployé votre application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], la nouvelle configuration ne sera chargée qu'au prochain intervalle d'interrogation. Toutefois, si vous configurez et redémarrez votre application, la configuration est immédiatement récupérée.  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a>Ajout de l'utilisateur au rôle approprié de l'activité BAM  
 L'infrastructure de l'intercepteur BAM utilise les rôles SQL Server par activité pour contrôler l'accès aux activités et aux informations de configuration. Vous devez ajouter le compte d'utilisateur exécutant votre application WCF au(x) rôle(s) approprié(s) de l'activité BAM dans la base de données BAMPrimaryImport.  
  
### <a name="configuring-the-windows-communication-foundation-application-to-load-the-bam-tracking-service"></a>Configuration de l'application Windows Communication Foundation pour charger le service de suivi BAM  
 Pour configurer l'application de manière qu'elle charge le service de suivi BAM, ajoutez quelques lignes au fichier App.config du serveur ou de l'application cliente.  
  
 Pour activer le suivi BAM sur votre serveur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] ou application cliente, vous devez modifier le fichier de configuration App.config en incluant un nouveau comportement de point de terminaison et une extension de comportement, et en ajoutant un attribut de configuration de comportement. Les formats du service et des modèles client sont similaires.  
  
 Lorsque vous configurez l'application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], notez les points suivants. Si plusieurs comportements de point de terminaison BAM sont définis dans le fichier App.config pour la même application (même client ou service), l'analyse BAM effectue les actions suivantes.  
  
-   Si les chaînes de connexion diffèrent, l'analyse BAM génère une exception.  
  
-   Si seul l'intervalle d'interrogation diffère, l'analyse BAM en sélectionne un et continue. Au moment de la conception, il n'est pas possible de déterminer celui qui sera sélectionné.  
  
> [!NOTE]
>  Si les chaînes de connexion sont identiques, c'est-à-dire qu'elles font référence au même ordinateur, le traitement BAM est normal.  
  
 L'exemple suivant de modèle App.config est configuré pour une application serveur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il définit un point de terminaison qui utilise un comportement personnalisé « bamEndpointBehavior » configuré pour utiliser l'intercepteur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Service.CreditCardAuthorization">  
      <!-- The endpoint will use the "bamEndpointBehavior" -->   
      <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    </service>  
  </services>  
  <bindings>  
    <wsDualHttpBinding>  
      <binding name="wsDualHttpBinding_ICreditCardAuthorization" transactionFlow="true" />  
    </wsDualHttpBinding>  
  </bindings>  
  <behaviors>  
    <endpointBehaviors>  
      <!-- Define a new behavior named "bamEndpointBehavior" -->  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <extensions>  
    <behaviorExtensions>  
      <!-- Define a new enpoint behavior extension using WCF interceptor -->  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
  </extensions>  
</system.serviceModel>  
```  
  
 Vous devez légèrement modifier ce modèle avant de l'utiliser dans votre propre fichier App.config.  
  
##### <a name="to-use-this-template-in-your-wcf-service-appconfig-file"></a>Pour utiliser ce modèle dans votre fichier App.config du service WCF  
  
1.  Ouvrez le fichier App.config associé à votre application. Vous pouvez utiliser Notepad.exe ou un autre éditeur de texte pour cette tâche.  
  
2.  Ajoutez l'extension de comportement [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior à l'élément `extensions` à l'aide du code XML suivant :  
  
    ```  
    <behaviorExtensions>  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
    ```  
  
    > [!NOTE]
    >  Vous pouvez adapter le nom de l'extension de comportement, « BamEndpointBehaviorExtension », à votre environnement.  
  
3.  Ajoutez un nouveau comportement de point de terminaison qui utilise la nouvelle extension de comportement à l'élément `behaviors`, à l'aide du code XML suivant. L'extension de comportement fournit une chaîne de connexion et un intervalle d'interrogation en secondes.  
  
    ```  
    <endpointBehaviors>  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
    ```  
  
     Remplacez la source de données par le nom de l'ordinateur hébergeant la base de données BamPrimaryImport dans votre environnement. Adaptez l'intervalle d'interrogation aux conditions requises ; un nombre élevé signifie que l'intercepteur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] mettra plus longtemps à détecter les modifications de configuration. Si vous avez modifié le nom de l'extension de comportement, utilisez-le pour remplacer « BamEndpointBehaviorExtension ».  
  
    > [!NOTE]
    >  Vous pouvez adapter le nom du comportement, « bamEndpointBehavior », à votre environnement.  
  
    > [!NOTE]
    >  Évitez d'utiliser une combinaison de nom d'utilisateur/mot de passe en texte clair lorsque vous spécifiez l'élément `ConnectionString`. Cela pourrait compromettre votre serveur de bases de données.  
  
    > [!NOTE]
    >  Vous devez spécifier un `PollingIntervalSec` supérieur ou égal à 5 (secondes). Si vous spécifiez une valeur inférieure ou omettez l'élément `PollingIntervalSec`, une erreur est générée et l'interception n'est pas configurée.  
  
4.  Ajoutez l'attribut `behaviorConfiguration` au point de terminaison que vous allez suivre et nommez le nouveau comportement :  
  
    ```  
    <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    ```  
  
    > [!NOTE]
    >  Si vous avez utilisé un autre nom de comportement, indiquez-le à la place.  
  
     Vous pouvez appliquer la configuration du comportement à plusieurs points de terminaison.  
  
5.  Enregistrez le fichier App.config modifié et redémarrez votre application.
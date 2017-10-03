---
title: "L’adaptateur HTTP (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: f3bd8172-15c4-42fa-aa17-e4bed9d4aba4
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4f443bf0b60f0bb90a914824b3922110ee1b300
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-biztalk-server-sample"></a>Adaptateur HTTP (exemple BizTalk Server)
L'exemple d'adaptateur HTTP illustre l'implémentation des paradigmes de communication de requête/réponse et de sollicitation/réponse utilisés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\AdaptersDevelopment\HttpAdapter\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|\Design-Time\Adapter Management|Contient le projet qui implémente la phase de conception de cet adaptateur.|  
|\Run-Time\HttpReceive|Contient le projet qui implémente le modèle de communication de l'adaptateur de requête/réponse. Il s'agit d'un récepteur isolé.|  
|\Run-Time\HttpSend|Contient le projet qui implémente le modèle de communication de l'adaptateur de type sollicitation/réponse.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Cet exemple est conçu comme une infrastructure que vous utilisez pour développer des adaptateurs personnalisés. Il peut arriver que BizTalk Server doive acheminer des messages vers une application personnalisée ou utiliser un protocole pour lequel aucun adaptateur natif n'est prévu. Des entreprises tierces ont élaboré des adaptateurs qui prennent en charge des protocoles supplémentaires, et vous souhaitez peut-être savoir s'il existe un adaptateur adapté à votre protocole avant d'écrire le vôtre. Si vous ne parvenez pas à trouver un adaptateur qui prenne en charge vos conditions de communication, il vous reste la possibilité de développer votre propre adaptateur.  
  
 L'écriture d'un adaptateur personnalisé peut se révéler difficile. Pour vous faciliter la tâche, Microsoft a développé une structure de base appelée Infrastructure d'adaptateurs. Vous pouvez vous baser sur cette infrastructure, de même que vous pouvez utiliser l'exemple de code source fourni dans le kit SDK de BizTalk Server.  Pour plus d’informations sur les adaptateurs personnalisés et l’infrastructure d’adaptateurs, reportez-vous à la **Voir aussi** section à la fin de ce document.  
  
## <a name="building-and-initializing-the-sample-adapter"></a>Création et initialisation de l'exemple d'adaptateur  
  
> [!IMPORTANT]
>  Si l'installation BizTalk est 64 bits ou si son emplacement a été modifié, les valeurs OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath doivent être modifiées en conséquence.  
  
#### <a name="to-build-and-initialize-the-http-adapter-sample"></a>Pour créer et initialiser l'exemple d'adaptateur HTTP  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersDevelopment\HttpAdapter  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compile HTTPAdapter et toutes ses dépendances.  
  
    -   Crée une application IIS utilisée par le côté récepteur de l'adaptateur.  
  
 Sous IIS port d'envoi, vous devez vérifier que l'identité du pool d'applications exécutant cette application IIS est membre des groupes suivants :  
  
-   groupe Utilisateurs d'hôtes BizTalk isolés ;  
  
-   groupe IIS_WPG.  
  
-   Sous IIS 7.0, vous devez migrer l’application fonctionne avec le mode .NET intégré. Vous pouvez migrer la configuration d’application, y compris le contenu de la \<httpHandlers > section de configuration, à l’aide de ce qui suit à partir d’une fenêtre de ligne de commande (la fenêtre doit être en cours d’exécution en tant qu’administrateur) :  
  
    ```  
    %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/HttpReceive"  
    ```  
  
-   Après avoir migré votre application, elle sera exécutée en mode classique et en mode .NET intégré, tout comme sur les plateformes de niveau inférieur.  
  
> [!NOTE]
>  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
> [!NOTE]
>  Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
> [!NOTE]
>  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="registering-the-sample-adapter"></a>Enregistrement de l'exemple d'adaptateur  
  
#### <a name="to-register-the-http-adapter-sample"></a>Pour enregistrer l'exemple d'adaptateur HTTP  
  
1.  Dans l’Explorateur Windows, accédez au lecteur d’installation pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis accédez à \<chemin d’accès des exemples > \AdaptersDevelopment\HTTPAdapter.  
  
2.  Pour ajouter l’exemple d’adaptateur au Registre, double-cliquez sur **HTTP.NET.reg**.  
  
    > [!NOTE]
    >  HTTP.NET.reg inclut des chemins d'accès codés en dur vers le répertoire d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous n'avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut ou si vous avez mis à niveau votre installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une version antérieure de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez modifier le fichier HTTP.NET.reg en y indiquant les chemins d'accès appropriés. Mettez à jour les chemins d'accès associés aux valeurs « OutboundAssemblyPath » et « AdapterMgmtAssemblyPath » afin qu'ils pointent vers l'emplacement exact des fichiers spécifiés.  
  
    > [!IMPORTANT]
    >  Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **HTTP.NET.reg** fichier de Registre.  
  
3.  Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK**.  
  
4.  Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.  
  
## <a name="installing-the-sample-adapter"></a>Installation de l'exemple d'adaptateur  
  
#### <a name="to-install-the-http-adapter-sample"></a>Pour installer l'exemple d'adaptateur HTTP  
  
1.  Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] d’arborescence, puis développez le **groupe BizTalk** d’arborescence, puis développez le **paramètres de plateforme** arborescence.  
  
3.  Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.  
  
4.  Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Nom|Type **HTTP.NET**.|  
    |Adaptateur|Sélectionnez **HTTP.NET** dans la liste déroulante.|  
    | Description|Type **exemple d’adaptateur HTTP.NET**.|  
  
5.  Cliquez sur **OK**.  
  
6.  L'adaptateur apparaît dans la liste des adaptateurs, dans la fenêtre droite de la console Administration de BizTalk.  
  
## <a name="stopping-and-restarting-the-host-instance"></a>Arrêt et redémarrage de l'instance de l'hôte  
  
#### <a name="to-stop-and-restart-the-host-instance-for-the-http-adapter-sample"></a>Pour arrêter et redémarrer l'instance de l'hôte pour l'exemple d'adaptateur HTTP  
  
1.  Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] , puis **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.  
  
3.  Dans le volet de résultats, cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **arrêter**.  
  
     L’état de l’instance d’hôte devient **arrêté**.  
  
4.  Dans le volet de résultats, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.  
  
 L'adaptateur HTTP.NET peut maintenant être utilisé par votre application. Lors de la configuration de l’adaptateur, le format de la **répertoire virtuel** propriété du transport est au format : /httpreceive/httpreceive.aspx?optionalQueryString.  
  
## <a name="comments"></a>Commentaires  
 Le fait de l’adaptateur HTTP.NET utilisation des classes BaseAdapter fournie dans  *\<exemples de chemin >*\AdaptersDevelopment\BaseAdapter\v1.0... 2\\. Les classes fournies dans le projet BaseAdapter sont conçues pour accélérer le développement de l'adaptateur. Pour plus d'informations sur les classes fournies, consultez les commentaires du code BaseAdapter.  
  
## <a name="see-also"></a>Voir aussi  
 [Inscription d’un adaptateur](../core/registering-an-adapter.md)   
 [Exemples d’adaptateurs - utilisation](../core/adapter-samples-usage.md)   
 [Développement d’adaptateurs personnalisés](../core/developing-custom-adapters.md)   
 [Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md)   
 [L’utilisation des outils de Framework adaptateur](../core/using-the-adapter-framework-tools.md)   
 [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)   
 [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)   
 [Comment déployer un adaptateur personnalisé](../core/how-to-deploy-a-custom-adapter.md)   
 [Conseils pour la conception de votre adaptateur.](../core/tips-for-designing-your-adapter.md)   
 [Configuration de l’adaptateur au moment du Design](../core/adapter-design-time-configuration.md)
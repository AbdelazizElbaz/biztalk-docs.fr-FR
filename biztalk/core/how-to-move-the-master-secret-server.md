---
title: "Comment déplacer le serveur de secret principal | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], migrating
- migrating, Master Secret server
- Master Secret server, migrating
ms.assetid: 2bc5137e-f81d-486d-bb91-7c5981896f79
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4158b59e3cce9664ca7c8c7d8ea4c5e3221b04b9
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-master-secret-server"></a>Déplacement du serveur de secret principal
La présente rubrique décrit les procédures que vous pouvez suivre pour déplacer le secret principal d'un serveur vers un autre et pour déplacer le secret principal d'un serveur vers un cluster Windows Server.  
  
### <a name="to-move-the-master-secret-from-one-server-to-another-server"></a>Pour déplacer le secret principal d'un serveur vers un autre  
  
1.  Installez le Serveur d'authentification unique de l'entreprise Microsoft sur le nouveau serveur de secret principal s'il n'est pas encore installé. Lancez le programme d’installation de Microsoft Enterprise unique serveur d’authentification à partir de \Platform\SSO\setup.exe sur le CD-ROM de BizTalk Server.  
  
2.  Configurez l'authentification unique de l'entreprise sur le nouveau serveur de secret principal si ce n'est déjà fait. Pour configurer l'authentification unique de l'entreprise, procédez comme suit :  
  
    1.  Ouvrez l'outil de configuration. Par défaut, l’outil de configuration se trouve dans \<lecteur\>: \Program Files\Enterprise unique signe-On\Configuration.exe.  
  
    2.  Cliquez pour sélectionner **Enterprise SSO** dans le volet gauche.  
  
    3.  Activez la case à cocher **activer Enterprise Single Sign-On sur cet ordinateur** dans le volet droit.  
  
    4.  Cliquez sur l’option à **joindre un système SSO existant**.  
  
    5.  Spécifiez les **nom du serveur** et **nom de la base de données** pour l’authentification unique les options de base de données.  
  
    6.  Spécifier le compte de service de l’authentification unique de l’entreprise existant pour le **entreprise unique serveur d’authentification pour le Service Windows** option.  
  
        > [!NOTE]
        >  Il doit s'agir d'un compte de domaine.  
  
    7.  Cliquez sur l’option à **appliquer la Configuration** et cliquez sur **configurer** dans la boîte de dialogue Assistant de Configuration pour terminer la configuration.  
  
    8.  Cliquez sur **Terminer** et fermer l’outil de Configuration.  
  
3.  Sauvegardez le secret principal existant en suivant les étapes de [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
4.  Modifiez le nom du serveur de secret principal dans la base de données d'authentification unique afin de référencer le nouveau serveur de secret principal. Par exemple, le nom du nouveau serveur de secret principal peut être **NewMSSServer**. Pour ce faire, procédez comme suit sur le serveur de secret principal original :  
  
    1.  Collez le code suivant dans un éditeur de texte tel que notepad.exe :  
  
        ```  
        <sso>  
        <globalInfo>  
        <secretServer>NewMSSServer</secretServer>  
        </globalInfo>  
        </sso>  
        ```  
  
    2.  Enregistrez le fichier en tant que fichier .xml. Par exemple, enregistrez le fichier sous **NewMSSServer.xml**.  
  
    3.  À l'invite de commandes, accédez au dossier d'installation des services d'authentification unique de l'entreprise. Par défaut, le dossier d’installation est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
    4.  Type **ssomanage - updatedb** *XMLFile* pour mettre à jour le nom du serveur de secret principal dans la base de données.  
  
        > [!NOTE]
        >  Remplacez *XMLFile* avec le nom du fichier .xml que vous avez enregistré.  
  
        > [!NOTE]
        >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Redémarrez le service d'authentification unique de l'entreprise sur le nouveau serveur de secret principal.  
  
6.  Restaurer le secret principal sauvegardé sur le nouveau serveur de secret principal en suivant les étapes dans [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md) sur le nouveau serveur de secret principal.  
  
### <a name="to-move-the-master-secret-from-one-server-to-a-windows-server-cluster"></a>Pour déplacer le secret principal à partir d'un serveur vers un cluster Windows Server  
  
1.  Installer et configurer le service SSO sur un cluster Windows Server en suivant les étapes dans [mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md). Effectuer toutes les étapes décrites dans cette rubrique, à l’exception de la procédure décrite dans la **restaurer le secret principal sur le deuxième nœud du cluster** section. Étant donné que vous allez déplacer le serveur de secret principal existant vers le cluster ne choisissez pas l’option à **créer un nouveau système SSO** lors de la configuration de l’authentification unique de l’entreprise sur les nœuds de cluster. Lors de la configuration de chaque nœud de cluster, dans le programme Configuration de BizTalk Server, définissez les options suivantes pour la fonctionnalité d'authentification unique de l'entreprise :  
  
    1.  Cochez la case à côté **activer Enterprise Single Sign-On sur cet ordinateur**.  
  
    2.  Cliquez sur l’option à **joindre un système SSO existant**.  
  
    3.  Entrez des valeurs pour le nom du serveur de base de données SSO et le nom de base de données existants.  
  
    4.  Lorsque vous spécifiez le compte à utiliser pour le service d'authentification unique de l'entreprise, entrez le compte de service SSO existant.  
  
2.  Copiez le fichier de sauvegarde du secret principal existant dans le dossier \Enterprise Single Sign-On sur chaque nœud de cluster.  
  
3.  Si ce cluster Windows Server doit héberger un ou plusieurs hôtes BizTalk en cluster, à l'aide de l'utilitaire de ligne de commande ssomanage, définissez comme nom du serveur d'authentification unique pour tous les utilisateurs le nom du serveur de secret principal en cluster. Cette commande doit être exécutée à partir du dossier d’installation de l’authentification unique de l’entreprise sur chaque serveur BizTalk Server dans le groupe. Par exemple, la ligne de commande suivante définit le nom du serveur d'authentification unique pour tous les utilisateurs sur le nom du serveur de secret principal en cluster :  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER* est un espace réservé pour le réseau réel nom de ressource qui est créé dans le groupe de clusters qui contient la ressource de serveur de secret principal en cluster ce scénario, tous les hôtes BizTalk doivent être créés en tant que ressources de cluster dans le même groupe de clusters que la ressource de service de l’authentification unique de l’entreprise en cluster. L'exécution d'une instance de l'hôte BizTalk sans cluster sur un nœud de cluster Windows Server où le service d'authentification unique de l'entreprise est en cluster n'est pas une configuration prise en charge. Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service d'authentification unique de l'entreprise en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend de ce service.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Dans l’administrateur de Cluster, cliquez sur le groupe de clusters qui contient la ressource de service de l’authentification unique de l’entreprise en cluster, puis cliquez sur **mettre en ligne** pour démarrer toutes les ressources dans le groupe de clusters.  
  
5.  Si ce Cluster Windows Server doit héberger un ou plusieurs hôtes BizTalk en cluster, mettre à jour le nom du serveur SSO accessible dans le **propriétés du groupe BizTalk** pour référencer le serveur de secret principal en cluster. Lancez **Administration de BizTalk Server**, cliquez sur le groupe BizTalk, puis sélectionnez le **propriétés** menu article, puis mettez à jour l’entrée de **nom du serveur SSO** sur  **OK**.  
  
    > [!NOTE]
    >  Dans ce scénario, tous les hôtes BizTalk doivent être créés comme ressources du cluster dans le même groupe de clusters que la ressource du service d'authentification unique de l'entreprise en cluster. L'exécution d'une instance de l'hôte BizTalk sans cluster sur un nœud de cluster Windows Server où le service d'authentification unique de l'entreprise est en cluster n'est pas une configuration prise en charge. Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service d'authentification unique de l'entreprise en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend de ce service.  
  
6.  Cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre hors connexion**, puis cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre en ligne**.  
  
    > [!NOTE]
    >  Si cette étape n’est pas terminée, tente de restaurer le secret principal ne peut pas réussir.  
  
7.  Restaurez le serveur principal sauvegardé sur chaque nœud du cluster Windows hébergeant le serveur de secret principal en cluster. Suivez les étapes de [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md) sur chaque nœud du cluster Windows hébergeant le serveur de secret principal en cluster.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion du secret principal](../core/managing-the-master-secret.md)
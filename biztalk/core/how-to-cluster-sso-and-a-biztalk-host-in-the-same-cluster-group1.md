---
title: "Mise en Cluster de l’authentification unique et un hôte BizTalk dans le même Group1 Cluster | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 413cc8f4-f343-4c1c-8b79-3b15cb4c101d
caps.latest.revision: "44"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a72b6e343d2e417a718c238181fefdea8e5cceba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-cluster-sso-and-a-biztalk-host-in-the-same-cluster-group"></a>mise en cluster de l'authentification unique et d'un hôte BizTalk dans le même groupe de clusters
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de regrouper un ou plusieurs hôtes BizTalk et le service de l'authentification unique de l'entreprise (SSO) sur le même cluster Windows Server.  
  
> [!NOTE]
>  Pour implémenter correctement cette stratégie, vous devez créer les instances de l'hôte BizTalk et le service SSO comme ressources du cluster dans le même groupe de clusters.  
  
 L'utilisation du Clustering Windows avec un ou plusieurs hôtes BizTalk et SSO tombe généralement dans l'une des catégories suivantes :  
  
1.  Clustering du serveur de secret principal SSO et d'un ou plusieurs hôtes BizTalk dans le même groupe de clusters.  
  
     Dans ce scénario, la dépendance entre les hôtes BizTalk en cluster et le service SSO en cluster est conservée afin que si le groupe de clusters est basculé, toutes les ressources déplacent avec le groupe.  
  
     Si le service SSO est configuré comme une ressource en cluster sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez créer un service Web IIS en cluster dans le même groupe de clusters. Cela est nécessaire pour s'assurer que toutes les instances de l'hôte isolées s'exécutent sur le même nœud de cluster que le service SSO. Cela garantit que tout adaptateur s'exécutant dans une instance de l'hôte isolée aura accès au service SSO, puisque les instances de l'hôte isolées s'exécutent dans IIS.  
  
    > [!NOTE]
    >  Si une instance sans cluster d’un hôte BizTalk est en cours d’exécution sur le même nœud de cluster qui exécute une instance en cluster du service SSO, l’instance en cluster du service SSO ne peut pas être basculé, sauf si l’instance sans cluster de l’hôte BizTalk est arrêté. Une instance sans cluster de l’hôte BizTalk maintient une dépendance sur l’instance en cluster du service SSO en cours d’exécution sur le nœud de cluster et empêche l’instance en cluster du service SSO de basculer. Il est donc recommandé de ne pas créer d'instance sans cluster d'un hôte BizTalk à exécuter sur le nœud de cluster exécutant une instance en cluster du service SSO.  
  
2.  Clustering du service SSO (serveur de secret non principal) et d'un ou plusieurs hôtes BizTalk dans le même groupe de clusters. Ce scénario requiert qu'un serveur de secret principal distant soit disponible. Dans ce scénario, la dépendance entre les hôtes BizTalk en cluster et le service SSO en cluster est maintenue de façon à ce qu'en cas de basculement du groupe de clusters, toutes les ressources soient déplacées avec le groupe.  
  
     Si le service SSO est configuré comme une ressource en cluster sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez créer un service Web IIS en cluster dans le même groupe de clusters. Cela est nécessaire pour s'assurer que toutes les instances de l'hôte isolées s'exécutent sur le même nœud de cluster que le service SSO. Cela garantit que tout adaptateur s'exécutant dans une instance de l'hôte isolée aura accès au service SSO, puisque les instances de l'hôte isolées s'exécutent dans IIS.  
  
    > [!NOTE]
    >  Si une instance sans cluster d'un hôte BizTalk s'exécute sur le même nœud de cluster qu'une instance en cluster du service SSO, le basculement de cette dernière n'est possible que si l'instance sans cluster de l'hôte BizTalk est arrêtée. Une instance sans cluster de l'hôte BizTalk maintient une dépendance sur l'instance en cluster du service SSO s'exécutant sur le nœud de cluster et empêche le basculement de l'instance en cluster du service SSO. Pour cette raison, il est recommandé que vous ne créez pas une instance sans cluster d’un hôte BizTalk pour s’exécuter sur le même nœud de cluster qui exécute une instance en cluster du service SSO.  
  
3.  Clustering d'un ou plusieurs hôtes BizTalk sur un cluster Windows Server sans clustering du service SSO. Dans ce scénario, un ou plusieurs hôtes BizTalk sont configurés comme ressources du cluster, mais le service SSO n'est pas configuré comme ressource en cluster. Cette conception offre une haute disponibilité pour les hôtes BizTalk en cluster, mais pas pour le service SSO. Dans ce scénario, une défaillance du service SSO sur un nœud entraîne la défaillance des composants de BizTalk Server qui dépendent du service SSO sur ce nœud. Pour plus d’informations sur la configuration d’un hôte BizTalk Server en tant que ressource de cluster, consultez [comment configurer un hôte BizTalk en tant que ressource de Cluster](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3).  
  
 Les procédures suivantes décrivent comment regrouper un hôte BizTalk et le service SSO dans le même cluster Windows Server.  
  
### <a name="to-cluster-a-biztalk-host-and-the-sso-master-secret-server-on-the-same-windows-server-cluster"></a>Pour mettre en cluster un hôte BizTalk et le serveur de secret principal du système SSO sur le même cluster Windows Server  
  
1.  Si le cluster n’est pas configuré avec une ressource Distributed Transaction Coordinator (MSDTC), de cluster MSDTC sur un cluster de basculement Windows Server en suivant les étapes dans [liste de vérification : création d’un MS DTC Resource dans un ordinateur Windows Server 2008 Cluster de basculement](http://go.microsoft.com/fwlink/p/?LinkID=129677) (http://go.microsoft.com/fwlink/p/?LinkID=129677).  
  
2.  Installer et configurer le service SSO sur le cluster Windows Server en suivant les étapes dans [mise en Cluster du serveur de secret principal](http://msdn.microsoft.com/library/59895616-4178-46d0-b9ff-95589b809ff5). Comme vous allez exécuter BizTalk Server sur le cluster Windows Server, installez tous les composants de BizTalk Server requis, même si, à ce stade, vous allez uniquement configurer les composants de SSO.  
  
3.  Mettre en cluster IIS sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur en suivant les étapes décrites dans [Base de connaissances Microsoft l’article 970759 « configuration IIS 7.0 dans un Microsoft Windows Server 2008 failover cluster »](http://go.microsoft.com/fwlink/p/?LinkId=152793) (http://go.microsoft.com/fwlink/p/?LinkId=152793). Créez le service Web IIS en cluster dans le même groupe de clusters que le service SSO en cluster.  
  
4.  Déplacer le groupe de clusters contenant le service SSO en cluster à un des nœuds du cluster et ouvrez une session sur ce nœud de cluster.  
  
5.  Démarrez le programme Configuration de BizTalk Server, puis effectuez la configuration de BizTalk Server sur ce nœud de cluster. Dans la mesure où il s’agit du premier ordinateur BizTalk Server dans le groupe, cliquez sur **créer un groupe BizTalk** lors de la configuration du groupe BizTalk.  
  
6.  Une fois la configuration de BizTalk Server correctement effectuée, déplacez le groupe de clusters contenant le service SSO en cluster vers l'autre nœud de cluster, puis connectez-vous à ce dernier.  
  
7.  Démarrez le programme Configuration de BizTalk Server, puis effectuez la configuration de BizTalk Server sur ce nœud de cluster. Cliquez sur **joindre un groupe BizTalk existant** lors de la configuration du composant groupe BizTalk sur ce nœud de cluster, puis spécifiez le groupe BizTalk que vous avez créé sur le premier nœud.  
  
8.  Une fois la configuration de BizTalk Server correctement effectuée, créez un ou plusieurs hôtes BizTalk en cluster en suivant les étapes dans [comment configurer un hôte BizTalk en tant que ressource de Cluster](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3).  
  
    > [!NOTE]
    >  Dans ce scénario, tous les hôtes BizTalk doivent être créés comme ressources du cluster dans le même groupe de clusters que la ressource du service SSO en cluster. Exécute une instance d’hôte BizTalk sans cluster sur un nœud de Cluster Windows Server où le service d’authentification unique est en cluster n’est pas une configuration prise en charge. Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service SSO en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend du service SSO.  
  
### <a name="to-cluster-a-biztalk-host-and-sso-non-master-secret-server-on-the-same-windows-server-cluster-when-the-sso-master-secret-server-is-remote"></a>Pour mettre en cluster un hôte BizTalk et le service SSO (serveur de secret non principal) sur le même cluster Windows Server quand le serveur de secret principal du système SSO est distant  
  
1.  Si le cluster n’est pas configuré avec une ressource Distributed Transaction Coordinator (MSDTC), de cluster MSDTC sur un cluster de basculement Windows Server en suivant les étapes dans [liste de vérification : création d’un MS DTC Resource dans un ordinateur Windows Server 2008 Cluster de basculement](http://go.microsoft.com/fwlink/p/?LinkID=129677) (http://go.microsoft.com/fwlink/p/?LinkID=129677).  
  
2.  Créer des groupes de domaine avec les noms **administrateurs SSO** et **administrateurs d’applications associées à authentification unique**. Pour créer une instance en cluster du service SSO, vous devez créer le **administrateurs SSO** et **administrateurs d’applications associées à authentification unique** groupes en tant que groupes de domaine.  
  
3.  Créez ou désignez un compte de domaine qui est membre de la **administrateurs SSO** groupe de domaine. Le service SSO sur chaque nœud sera configuré pour ouvrir une session en tant que ce compte de domaine. Ce compte doit avoir le **ouvrir une session en tant que service** à droite sur chaque nœud du cluster.  
  
4.  Ajoutez le compte que vous utilisez pour vous connecter pendant le processus d’installation et de configuration pour le domaine **administrateurs SSO** groupe.  
  
    > [!IMPORTANT]
    >  La configuration du service SSO échoue si les étapes 3 et 4 ne sont pas terminées.  
  
5.  Ouvrez une session sur un des nœuds de cluster, puis installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Sélectionnez l'option pour démarrer le programme de configuration une fois l'installation correctement effectuée.  
  
6.  Choisissez le **Configuration personnalisée** option et entrez les valeurs appropriées pour le **nom du serveur de base de données**, **nom d’utilisateur** et **mot de passe**champs. Après avoir entré ces valeurs, cliquez sur le **configurer** pour continuer.  
  
7.  Définissez les options suivantes pour la fonction SSO :  
  
    1.  Activez la case à cocher en regard **activer Enterprise Single Sign-On sur cet ordinateur**.  
  
    2.  Cliquez sur l’option à **joindre un système SSO existant**.  
  
    3.  Entrez des valeurs pour le nom du serveur de base de données SSO et le nom de base de données existants.  
  
    4.  Entrez le compte de service d’authentification unique existant lorsque vous spécifiez le compte à utiliser pour le service Enterprise Single Sign-On.  
  
8.  Comme il s’agit du premier serveur BizTalk dans le groupe, sélectionnez l’option **créer un groupe BizTalk** lors de la configuration du composant groupe BizTalk.  
  
9. Spécifiez les options de configuration restantes nécessaires, puis appliquez la configuration de BizTalk Server à ce nœud.  
  
10. Une fois la configuration de BizTalk Server correctement effectuée sur le premier nœud, ouvrez une session sur le second, puis installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Sélectionnez l'option pour démarrer le programme de configuration une fois l'installation correctement effectuée.  
  
11. Choisissez le **Configuration personnalisée** option et entrez les valeurs appropriées pour le **nom du serveur de base de données**, **nom d’utilisateur** et **mot de passe** champs. Après avoir entré ces valeurs, cliquez sur le **configurer** pour continuer.  
  
12. Définissez les options suivantes pour la fonction SSO :  
  
    1.  Activez la case à cocher en regard **activer Enterprise Single Sign-On sur cet ordinateur**.  
  
    2.  Cliquez sur **joindre un système SSO existant**.  
  
    3.  Entrez des valeurs pour le nom du serveur de base de données SSO et le nom de base de données existants.  
  
    4.  Entrez le compte de service d’authentification unique existant lorsque vous spécifiez le compte à utiliser pour le service Enterprise Single Sign-On.  
  
13. Choisissez l’option **joindre un groupe BizTalk existant** lors de la configuration du composant groupe BizTalk sur ce nœud de cluster, puis spécifiez le groupe BizTalk que vous avez créé sur le premier nœud.  
  
14. Spécifiez les options de configuration restantes nécessaires, puis appliquez la configuration de BizTalk Server à ce nœud.  
  
15. Une fois la configuration de BizTalk Server terminée, procédez comme suit pour mettre en cluster le service d’authentification unique :  
  
    1.  Arrêtez le service SSO sur chaque nœud de cluster en tapant ce qui suit à partir d'une invite de commandes :  
  
        ```  
        net stop entsso  
        ```  
  
    2.  Dans Gestion du cluster de basculement, déplacez tous les groupes de cluster vers un seul nœud, puis ouvrez une session sur ce dernier.  
  
    3.  Dans le volet gauche, cliquez pour sélectionner un service ou une application en cluster, contenant une ressource Nom de réseau et une ressource Adresse IP. Ce service ou cette application en cluster contiendra le service SSO en cluster et l'hôte BizTalk en cluster.  
  
        > [!NOTE]
        >  Un service SSO en cluster ne requiert pas explicitement l'utilisation d'une ressource Disque physique en cluster dans le même groupe.  
  
    4.  Avec le bouton droit de l’application ou le service en cluster, pointez sur **ajouter une ressource**, puis cliquez sur **Service générique** pour afficher les **Assistant Nouvelle ressource** boîte de dialogue.  
  
    5.  Sur le **sélectionner un Service** page de la **Assistant Nouvelle ressource**, sélectionnez **Enterprise Single Sign-On Service**, puis cliquez sur **suivant**.  
  
    6.  Sur le **Confirmation** page, cliquez sur **suivant**.  
  
    7.  Sur le **Résumé** page, cliquez sur **Terminer**. Une instance en cluster de l’entreprise Sign-On Service unique s’affiche sous **autres ressources** dans le volet central de la **gestion du Cluster de basculement** interface.  
  
    8.  Avec le bouton droit de l’instance en cluster de l’entreprise Sign-On Service unique et sélectionnez **propriétés** pour afficher les **entreprise unique Sign-On Service Properties** boîte de dialogue.  
  
    9. Cliquez sur le **dépendances** onglet de la boîte de dialogue Propriétés et cliquez sur **insérer**.  
  
    10. Cliquez sur la zone de liste déroulante sous **ressource**, sélectionnez le **nom :** ressource et cliquez sur **OK**.  
  
        > [!IMPORTANT]
        >  Si vous n’ajoutez pas de dépendance à la **nom :** ressource, les ordinateurs clients SSO génère une erreur semblable au suivant quand ils tentent de contacter cette instance en cluster du service d’authentification unique :  
        >   
        >  Impossible d'extraire les secrets principaux.  
        >   
        >  Vérifiez que le nom de serveur de secret principal est correct et disponible. Nom du serveur de secret : Code d'erreur ENTSSO : 0x800706D9, le mappeur de point final n'a plus de point final disponible.  
  
16. Mettre en cluster IIS sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur en suivant les étapes décrites dans [Base de connaissances Microsoft l’article 970759 « configuration IIS 7.0 dans un Microsoft Windows Server 2008 failover cluster »](http://go.microsoft.com/fwlink/p/?LinkId=152793) (http://go.microsoft.com/fwlink/p/?LinkId=152793). Créer le service web IIS en cluster dans le même groupe de clusters en tant que le service SSO en cluster.  
  
17. Dans la gestion du Cluster de basculement, avec le bouton droit sur le service en cluster ou l’application qui contient le service Enterprise Single Sign-On en cluster et sélectionnez **mettre ce service ou cette application en ligne** pour démarrer toutes les ressources dans le service de cluster ou l’application.  
  
18. Avec le bouton droit de l’application ou le service en cluster, pointez sur **déplacer ce service ou cette application vers un autre nœud**, puis cliquez sur le second nœud. Cette opération déplace le service ou l'application en cluster contenant le service d'authentification unique de l'entreprise en cluster du premier nœud vers le second.  
  
19. Cliquez sur le service Enterprise Single Sign-On en cluster, sur **hors connexion ce service ou cette application**, puis cliquez sur l’instance en cluster du service SSO, sur **mettre ce service ou application en ligne**.  
  
20. Définir le nom du serveur SSO pour tous les utilisateurs pour le service SSO en cluster avec l’utilitaire de ligne de commande ssomanage. Vous devez exécuter cette commande à partir du dossier d'installation de SSO sur chaque serveur BizTalk du groupe. Par exemple, la ligne de commande suivante définit le nom de serveur SSO pour tous les utilisateurs sur le service SSO en cluster :  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER* est un espace réservé pour la ressource de nom de réseau réelle créée dans le groupe de clusters contenant le service SSO en cluster.  
  
21. Mettre à jour le nom du serveur SSO accessible dans le **propriétés du groupe BizTalk** pour référencer le service SSO en cluster. Ouvrez **Administration de BizTalk Server**, cliquez sur le groupe BizTalk, sélectionnez le **propriétés** l’élément de menu, mettre à jour l’entrée pour le nom du serveur d’authentification unique, puis cliquez sur **OK**.  
  
22. Suivez les étapes de [comment configurer un hôte BizTalk en tant que ressource de Cluster](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3) pour créer une ou plusieurs instances en cluster de l’hôte BizTalk du même groupe de clusters que vous avez créé le service SSO en cluster.  
  
    > [!NOTE]
    >  Dans ce scénario, tous les hôtes BizTalk doivent être créés comme ressources du cluster dans le même groupe de clusters que la ressource du service SSO en cluster. L'exécution d'une instance de l'hôte BizTalk sans cluster sur un nœud de cluster Windows Server où le service SSO est en cluster n'est pas une configuration prise en charge. Cela est dû au fait que l'exécution de l'instance de l'hôte BizTalk sans cluster échouera lors du basculement du service SSO en cluster vers un autre nœud, parce qu'une instance de l'hôte BizTalk dépend du service SSO.
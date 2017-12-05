---
title: Mise en Cluster le serveur1 Secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, second node
- Master Secret server, restoring
- clustering, Master Secret server
- Master Secret server, clustering
ms.assetid: ef817fa4-e43d-4e3d-8686-5bd675708001
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9740bb1c73dd5f416dda3c2f29bb15fbc7241a51
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-cluster-the-master-secret-server"></a>Mise en Cluster du serveur de secret principal
Il est recommandé de suivre les instructions dans cette section pour mettre en cluster le service d'authentification unique de l'entreprise sur le serveur de secret principal.  
  
 Lorsque vous mettez en cluster le serveur de secret principal, les serveurs d'authentification unique communiquent avec l'instance en cluster active sur le serveur de secret principal. De même, l'instance en cluster active du serveur de secret principal communique avec la base de données de l'authentification unique.  
  
 Seul un administrateur de l'authentification unique peut effectuer cette procédure.  
  
> [!CAUTION]
>  Vous ne pouvez pas installer le serveur de secret principal sur un cluster d'équilibrage de la charge réseau.  
  
### <a name="to-install-and-configure-enterprise-sso-on-the-cluster-nodes"></a>Pour installer et configurer l'authentification unique de l'entreprise sur les nœuds de cluster  
  
1.  Installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur chaque nœud de cluster. Dans **Installation des composants**, sélectionnez **unique Sign-On Administration entreprise** et **entreprise seule l’authentification serveur de secret principal**. Une fois l’installation est terminée, procédez comme **pas** exécuter la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration.  
  
2.  Créer **administrateurs SSO** et **administrateurs d’applications associées à authentification unique** groupes de domaine. Pour créer une instance en cluster du service d'authentification unique de l'entreprise, vous devez créer ces groupes en tant que groupes de domaines.  
  
3.  Créez ou désignez un compte de domaine qui est membre de la **administrateurs SSO** groupe de domaine. Le service d'authentification unique de l'entreprise sur chaque nœud est configuré pour ouvrir une session en tant que ce compte de domaine. Ce compte doit avoir le **ouvrir une session en tant que service** à droite sur chaque nœud du cluster.  
  
4.  Ajoutez le compte que vous utilisez pour vous connecter pendant le processus de configuration pour le domaine **administrateurs SSO** groupe.  
  
    > [!IMPORTANT]
    >  La configuration du service d'authentification unique de l'entreprise échoue si les étapes 3 et 4 ne sont pas terminées.  
  
5.  Démarrez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
6.  Sélectionnez **Configuration personnalisée** et entrez le **nom du serveur de base de données**, **nom d’utilisateur**, et **mot de passe** valeurs. Sélectionnez **configurer** pour continuer.  
  
    > [!NOTE]
    >  Comme vous configurez uniquement le service d'authentification unique de l'entreprise à ce moment, vous pouvez simplement entrer le compte de domaine créé précédemment.  
  
7.  Sélectionnez le **Enterprise SSO** option dans le volet gauche et définissez les options suivantes pour la fonctionnalité de l’authentification unique de l’entreprise :  
  
    1.  Sélectionnez le **activer Enterprise Single Sign-On sur cet ordinateur** case à cocher.  
  
    2.  Sélectionnez **créer un nouveau système SSO**.  
  
    3.  Entrez le **stocke les données** pour **nom du serveur** et **nom de la base de données** valeurs.  
  
    4.  Vérifiez que le compte de domaine créé précédemment est le compte associé au service d'authentification unique de l'entreprise.  
  
    5.  Entrez le groupe Administrateurs de l'authentification unique du domaine créé précédemment comme groupe associé au rôle Administrateur(s) de l'authentification unique.  
  
    6.  Entrez le groupe Administrateurs d'applications associées à authentification unique du domaine créé précédemment comme groupe associé au rôle Administrateur(s) d'applications associées à authentification unique.  
  
8.  Sélectionnez le **sauvegarde du Secret Enterprise SSO** option dans le volet gauche et fournissez les paramètres appropriés pour sauvegarder le secret de l’authentification unique de l’entreprise. Par défaut, le secret de l’authentification unique de l’entreprise est sauvegardé sur  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On\\*SSOxxxx*.bak.  
  
9. Cliquez sur le **appliquer la Configuration** et passez en revue le résumé.  
  
10. Cliquez sur **suivant** pour appliquer la configuration.  
  
11. Cliquez sur **Terminer** pour fermer l’Assistant de Configuration.  
  
12. Fermez la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
13. Ouvrez une session sur le nœud de cluster passif, puis démarrez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
14. Choisissez le **Configuration personnalisée** et entrez les mêmes valeurs pour le **nom du serveur de base de données**, **nom d’utilisateur**, et **mot de passe** qui vous avez entré lors de la configuration du premier nœud du cluster. Après avoir entré ces valeurs, cliquez sur **configurer** pour continuer.  
  
15. Sélectionnez le **Enterprise SSO** option dans le volet gauche et définissez les options suivantes pour la fonctionnalité de l’authentification unique de l’entreprise :  
  
    1.  Sélectionnez le **activer Enterprise Single Sign-On sur cet ordinateur** option.  
  
    2.  Sélectionnez **joindre un système SSO existant**.  
  
    3.  Entrez les mêmes valeurs pour la base de données SSO **nom du serveur** et **nom de la base de données** que vous avez entré lors de la configuration du premier nœud du cluster.  
  
    4.  Entrez la même valeur pour le compte de domaine que celle entrée lors de la configuration du premier nœud de cluster.  
  
16. Sélectionnez **appliquer la Configuration** pour afficher le résumé.  
  
17. Sélectionnez **suivant** pour appliquer la configuration.  
  
18. Sélectionnez **Terminer** pour fermer l’Assistant de Configuration.  
  
19. Fermez la Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-update-the-master-secret-server-name-in-the-sso-database"></a>Pour mettre à jour le nom du serveur de secret principal dans la base de données d'authentification unique  
  
1.  Tapez les commandes suivantes dans une invite de commandes sur le nœud de cluster actif pour arrêter et redémarrer le service d'authentification unique de l'entreprise :  
  
    ```  
    net stop entsso  
    ```  
  
     et  
  
    ```  
    net start entsso  
    ```  
  
2.  Modifiez le nom du serveur de secret principal dans la base de données d'authentification unique par le nom du cluster en procédant comme suit :  
  
    > [!NOTE]
    >  Le nom du cluster est celui défini pour la ressource de nom de réseau créée dans le groupe de clusters/le service ou l'application en cluster qui contiendra le service d'authentification unique de l'entreprise en cluster. Par exemple, le nom peut être *CLUSTERBIZTALK*.  
  
    1.  Collez le code suivant dans un éditeur de texte :  
  
        ```  
        <sso>  
          <globalInfo>  
            <secretServer>BIZTALKCLUSTER</secretServer>  
          </globalInfo>  
        </sso>  
        ```  
  
        > [!NOTE]
        >  *BIZTALKCLUSTER* est un espace réservé pour la ressource de nom de réseau réelle créée dans le cluster group / cluster le service ou application.  
  
    2.  Enregistrez le fichier au format .xml. Par exemple, enregistrez le fichier sous SSOCLUSTER.xml.  
  
    3.  À l'invite de commandes, accédez au dossier d'installation des services d'authentification unique de l'entreprise. Par défaut, le dossier d’installation est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
    4.  Tapez la commande suivante à l'invite de commandes pour mettre à jour le nom du serveur de secret principal dans la base de données :  
  
        ```  
        ssomanage -updatedb XMLFile  
        ```  
  
        > [!NOTE]
        >  *XMLFile* est un espace réservé pour le nom du fichier .xml que vous avez enregistré précédemment.  
  
### <a name="to-create-the-clustered-enterprise-sso-resource"></a>Pour créer la ressource d'authentification unique de l'entreprise en cluster  
  
1.  Si le cluster n’est pas configuré avec une ressource Distributed Transaction Coordinator (MSDTC) puis suivez les étapes décrites dans le livre blanc « Amélioration erreur la tolérance de panne dans BizTalk Server par Using a Windows Server Cluster » [http:// go.Microsoft.com/fwlink/ ? LinkId = 69207](http://go.microsoft.com/fwlink/?LinkId=69207) pour créer une ressource MSDTC en cluster.  
  
2.  Cliquez sur **Démarrer**, **programmes**, **outils d’administration**, puis **gestion du Cluster de basculement** pour démarrer le Cluster de basculement Programme de gestion.  
  
3.  Dans le volet gauche, cliquez sur **gestion du Cluster de basculement** et cliquez sur **gérer un Cluster**.  
  
4.  Sur le **sélectionner un cluster à gérer** boîte de dialogue, entrez le cluster pour être géré et cliquez sur **OK**.  
  
5.  Dans le volet gauche, cliquez pour sélectionner un service ou une application en cluster, contenant une ressource Nom de réseau et une ressource Adresse IP. Suivez les étapes de [la création d’un groupe de clusters avec un disque, une adresse IP et une ressource de nom](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md) pour créer un groupe avec une ressource d’adresse IP et nom de réseau si elle n’existe pas déjà.  
  
    > [!NOTE]
    >  Un service SSO en cluster n’exige pas explicitement l’utilisation d’une ressource de disque physique en cluster dans le même groupe.  
  
6.  Avec le bouton droit de l’application ou le service en cluster, pointez sur **ajouter une ressource**, puis cliquez sur **Service générique** pour afficher les **Assistant Nouvelle ressource** boîte de dialogue.  
  
    > [!IMPORTANT]
    >  Dans le **paramètres de Service générique** boîte de dialogue, si vous ne cliquez pas sur pour sélectionner le **utiliser le nom réseau pour le nom de l’ordinateur** case à cocher, ordinateurs clients SSO génère une erreur semblable au suivant lorsqu’ils Essayez de contacter cette instance en cluster du service SSO de l’entreprise :  
    >   
    >  Impossible d'extraire les secrets principaux.  
    >   
    >  Vérifiez que le nom de serveur de secret principal est correct et disponible. Nom du serveur de secret : Code d'erreur ENTSSO : 0x800706D9, le mappeur de point final n'a plus de point final disponible.  
  
7.  Sur le **sélectionner un Service** page de la **Assistant Nouvelle ressource**, sélectionnez **Enterprise Single Sign-On Service** et cliquez sur **suivant**.  
  
8.  Sur le **Confirmation** page, cliquez sur **suivant**.  
  
9. Sur le **Résumé** page, cliquez sur **Terminer**. Une instance en cluster de l’entreprise Sign-On Service unique s’affiche sous **autres ressources** dans le volet central de la **gestion du Cluster de basculement** interface.  
  
10. Avec le bouton droit de l’instance en cluster de l’entreprise Sign-On Service unique et sélectionnez **propriétés** pour afficher les **entreprise unique Sign-On Service Properties** boîte de dialogue.  
  
11. Cliquez sur le **dépendances** onglet de la boîte de dialogue Propriétés et cliquez sur **insérer**.  
  
12. Cliquez sur la zone de liste déroulante sous **ressource**, sélectionnez le **nom :** ressource et cliquez sur **OK**.  
  
### <a name="to-restore-the-master-secret-on-the-second-cluster-node"></a>Pour restaurer le secret principal sur le second nœud de cluster  
  
1.  Dans la gestion du Cluster de basculement, avec le bouton droit sur le service en cluster ou l’application qui contient le service Enterprise Single Sign-On en cluster et sélectionnez **mettre ce service ou cette application en ligne** pour démarrer toutes les ressources dans le service de cluster ou l’application.  
  
2.  Avec le bouton droit de l’application ou le service en cluster, pointez sur **déplacer ce service ou cette application vers un autre nœud**, puis cliquez sur le second nœud. Cette opération déplace le service ou l'application en cluster contenant le service d'authentification unique de l'entreprise en cluster du premier nœud vers le second.  
  
3.  Cliquez sur le service Enterprise Single Sign-On en cluster, sur **hors connexion ce service ou cette application**, puis cliquez sur l’instance en cluster du service SSO de l’entreprise, sur **mettre ce service ou application en ligne**.  
  
    > [!NOTE]
    >  Si cette étape n'est pas achevée, les tentatives de restauration du secret principal risquent d'échouer.  
  
4.  Copiez le fichier de sauvegarde du secret principal du premier nœud dans le dossier d'installation \Enterprise Single Sign-On sur le second nœud. Par défaut, le dossier d’installation est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
5.  Ouvrez une session sur le second nœud, ouvrez une invite de commandes, puis accédez au dossier d'installation des services d'authentification unique de l'entreprise.  
  
6.  Tapez la commande suivante à l'invite de commandes pour restaurer le secret principal sur le second nœud :  
  
    ```  
    ssoconfig -restoresecret RestoreFile  
    ```  
  
    > [!NOTE]
    >  Remplacez *RestoreFile* avec le chemin d’accès et le nom du fichier de sauvegarde qui contient le secret principal.  
  
     Le serveur principal est stocké dans le Registre à l'emplacement suivant :  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
7.  Déplacez le service ou l'application en cluster contenant le service d'authentification unique de l'entreprise en cluster de ce nœud vers l'autre nœud du cluster pour assurer la fonctionnalité de basculement. Replacez ensuite le groupe de clusters dans sa position d'origine pour vérifier la fonctionnalité de restauration.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un groupe de clusters avec un disque, une adresse IP et une ressource de nom](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)

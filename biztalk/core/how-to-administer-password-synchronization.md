---
title: Comment administrer la synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], applications
- Password Synchronization [SSO], notifications
- applications, Password Synchronization [SSO]
- SSOPS command line utility [SSO]
- administering, Password Synchronization [SSO]
- Password Synchronization [SSO], adapters
- Password Synchronization [SSO], administering
- notifications [SSO]
- Password Synchronization [SSO], SSOPS command line utility
ms.assetid: e5568cc2-7530-452c-9902-d7ffcad66088
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd696da8b4cab24a8de6a4b5d8ac8f26856f7e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-administer-password-synchronization"></a>Comment administrer la synchronisation de mot de passe
Vous pouvez administrer la synchronisation de mot de passe via le composant logiciel enfichable MMC ou la ligne de commande.  
  
 Le composant logiciel enfichable MMC affiche une liste des adaptateurs et de leurs propriétés. Vous pouvez cliquer avec le bouton droit sur un adaptateur et utiliser le menu pour exécuter les commandes suivantes :  
  
-   Créer des adaptateurs  
  
-   Définir les propriétés  
  
-   Update  
  
-   DELETE  
  
-   Activer  
  
-   Désactiver  
  
-   Ajouter des applications à un adaptateur  
  
-   Supprimer des applications d'un adaptateur  
  
-   Réinitialiser la notification  
  
-   Ajouter un adaptateur à un groupe d'adaptateurs  
  
-   Supprimer une carte à partir d’un groupe d’adaptateurs  
  
 Vous pouvez également utiliser l'utilitaire de ligne de commande SSOPS pour administrer la synchronisation de votre mot de passe. La plupart des commandes de cette section sont destinées à être utilisées par un administrateur uniquement.  
  
 Pour de nombreuses commandes, le résultat de la commande s'affiche à l'écran en deux colonnes. Comme les paramètres de certains écrans peuvent tronquer les données, pour des résultats optimaux, vous devez passer la taille de la mémoire tampon écran / taille Windows à 120 caractères.  
  
 Les commandes SSOPS sont répertoriées dans le tableau suivant. Les procédures et des explications supplémentaires sont situées dans le reste de cette rubrique.  
  
|Command|Fonction|  
|-------------|--------------|  
|-list|Répertorie les adaptateurs existants.|  
|-display|Affiche les informations relatives aux adaptateurs|  
|-create|Crée des adaptateurs|  
|-setprops|Définit les propriétés de l'adaptateur|  
|-update|Met à jour le ou les adaptateurs existants|  
|-delete|Supprime un adaptateur existant|  
|-enable|Active l'adaptateur|  
|-disable|Désactive l'adaptateur|  
|-addapp|Ajoute l'application à l'adaptateur|  
|-deleteapp|Supprime l'application de l'adaptateur|  
|-reset|Réinitialise la notification ou les files d'attente d'amortissement|  
|-addtogroup|Ajoute l'adaptateur au groupe d'adaptateurs|  
|-deletefromgroup|Supprime l'adaptateur du groupe d'adaptateurs|  
  
### <a name="to-list-existing-adapters"></a>Pour répertorier les adaptateurs existants  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-liste** et appuyez sur ENTRÉE.  
  
     Les adaptateurs et leurs descriptions sont répertoriés. (E) indique que l'adaptateur est activé, (D) indique qu'il est désactivé.  
  
### <a name="to-display-adapter-information"></a>Pour afficher les informations sur l'adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-afficher \<nom de l’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     La sortie écran affiche les informations concernant l'adaptateur spécifié.  
  
     En plus du nom, du type, de la description, de l'ordinateur et des comptes, les informations suivantes s'affichent.  
  
    |Indicateur de l'adaptateur|Détails|  
    |------------------|-------------|  
    |Adaptateur activé|Détermine si l'adaptateur est activé.<br /><br /> Indicateur : SSO_FLAG_ENABLED<br /><br /> Nom d’attribut : enableApp<br /><br /> Par défaut : aucun|  
    |Autoriser les comptes locaux|Détermine si les comptes des administrateurs et des utilisateurs d'application (App Admin et App Users) peuvent être des comptes locaux.<br /><br /> Indicateur : SSO_FLAG_APP_ALLOW_LOCAL<br /><br /> Nom d’attribut : allowLocalAccounts<br /><br /> Par défaut : aucun|  
    |Recevoir les modifications du mot de passe de l'adaptateur|Détermine si l'adaptateur est autorisé à recevoir des modifications de mot de passe externes.<br /><br /> Indicateur : (sso_flag_partial_sync_from_external_to_db)<br /><br /> Nom d’attribut : syncFromAdapter<br /><br /> Par défaut : aucun|  
    |Vérifier l'ancien mot de passe|Détermine si l'adaptateur doit vérifier l'ancien mot de passe lorsqu'une modification de mot de passe externe est reçue. Lorsqu'un mot de passe externe est modifié et que cet indicateur est défini, l'adaptateur externe doit fournir l'ancien mot de passe externe ainsi que le nouveau. L'ancien mot de passe externe est ensuite comparé au mot de passe externe existant pour ce compte externe dans la base de données SSO. S'ils correspondent, la modification est acceptée. Sinon, la modification est rejetée.<br /><br /> Indicateur : SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS<br /><br /> Nom d’attribut : verifyOldPassword<br /><br /> Par défaut : Oui|  
    |Modifier le mot de passe Windows|Détermine si le mot de passe Windows doit également être modifié lorsqu'une modification de mot de passe externe est reçue (synchronisation complète). ENTSSO utilise toujours l'ancien mot de passe Windows stocké dans la base de données SSO pour remplacer le mot de passe Windows par la nouvelle valeur (Windows requiert les nouveau et ancien mots de passe pour modifier le mot de passe d'un utilisateur). Il doit donc être initialisé afin que la modification de mot de passe Windows puisse réussir. Si la synchronisation de mot de passe est configurée pour un mappage particulier, lorsque les informations d’identification externes sont définies via des outils administratifs (ssomanage ou ssoclient - setcredentials) le mot de passe Windows stocké dans la base de données SSO est également défini. Indicateur : SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS<br /><br /> Nom d’attribut : changeWindowsPassword<br /><br /> Par défaut : aucun|  
    |Envoyer les modifications du mot de passe Windows à l'adaptateur|Détermine si la modification de mot de passe Windows doit être envoyée à l'adaptateur externe.<br /><br /> Indicateur : SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL<br /><br /> Nom d’attribut : syncToAdapter<br /><br /> Par défaut : aucun|  
    |Envoyer l'ancien mot de passe à l'adaptateur|Si Oui, la valeur entrée pour l'ancien mot de passe (dans la base de données SSO) est envoyée à l'adaptateur externe, de même que la valeur entrée pour le nouveau mot de passe. Certains systèmes externes requièrent en effet les deux mots de passe (le nouveau et l'ancien) pour réaliser la modification.<br /><br /> Indicateur : SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS<br /><br /> Nom d’attribut : sendOldPassword<br /><br /> Par défaut : aucun|  
    |Autoriser les conflits de mappage|Détermine si l'adaptateur autorise les conflits de mappage.<br /><br /> Un conflit survient lorsque les mappages ne sont pas uniques. Dans une seule application SSO individuels, les mappages sont toujours un à un : un compte Windows est mappé à un seul compte externe et vice versa.<br /><br /> En revanche, il est possible d'affecter plusieurs applications à un adaptateur. Par conséquent, il se peut qu'un mappage d'une application entre en conflit avec un mappage d'une autre application.<br /><br /> La fonction de cet indicateur vise à éviter que cela ne se produise. Il est conseillé de ne pas autoriser les conflits de mappage sauf si une condition particulière bien maîtrisée l'exige.<br /><br /> Indicateur : SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS<br /><br /> Nom d’attribut : allowMappingConflicts<br /><br /> Par défaut : aucun|  
  
    |Description de l'adaptateur|Détails|  
    |-------------------------|-------------|  
    |Nombre de tentatives de notification|Valeur par défaut est 1.|  
    |Délai de nouvelle tentative de notification (en minutes)|La valeur par défaut est 5.|  
    |Nombre maximal de notifications en attente|Valeur par défaut est 8.|  
    |Stocker les notifications (hors connexion)|True/False.|  
    |Nom du serveur|Nom du serveur.|  
    |Numéro de port|Numéro du port.|  
    |Applications pour cet adaptateur|Liste des applications actuellement affectées à l'adaptateur.|  
  
### <a name="to-create-new-adapters"></a>Pour créer des adaptateurs  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-créer \<fichier d’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     La sortie écran affiche les informations concernant l'adaptateur créé.  
  
### <a name="to-set-properties-for-an-adapter"></a>Pour définir les propriétés d'un adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops - setprops \<nom de l’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     La sortie écran affiche les propriétés de l'adaptateur spécifié. Vous pouvez les modifier si nécessaire, mais les nouvelles valeurs ne sont pas validées.  
  
### <a name="to-update-existing-adapters"></a>Pour mettre à jour des adaptateurs existants  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-mettre à jour \<fichier d’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     Utilisez cette commande pour mettre à jour les paramètres et indicateurs pour un adaptateur spécifié. N'utilisez pas cette commande pour définir les propriétés. Utilisez plutôt la commande -setprops.  
  
### <a name="to-delete-an-existing-adapter"></a>Pour supprimer un adaptateur existant  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-supprimer \<nom de l’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     L'adaptateur spécifié est supprimé.  
  
### <a name="to-enable-an-adapter"></a>Pour activer un adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-activer \<nom de l’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     L'adaptateur spécifié est activé.  
  
### <a name="to-disable-an-adapter"></a>Pour désactiver un adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-désactiver \<nom de l’adaptateur\>**  et appuyez sur ENTRÉE.  
  
     L'adaptateur spécifié est désactivé.  
  
### <a name="to-add-an-application-to-an-adapter"></a>Pour ajouter une application à un adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops - addapp \<nom de l’adaptateur\> \<nom de l’application\>**  et appuyez sur ENTRÉE.  
  
     L'application SSO spécifiée est affectée à l'adaptateur spécifié. Cela signifie que les mots de passe pour les mappages dans cette application sont désormais synchronisés à l'aide de cet adaptateur.  
  
     Alors que plusieurs applications peuvent être affectées à un seul adaptateur, une application donnée peut uniquement être affectée à un seul adaptateur.  
  
### <a name="to-delete-an-application-from-an-adapter"></a>Pour supprimer une application d'un adaptateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops - deleteapp \<nom de l’application\>**  et appuyez sur ENTRÉE.  
  
     L'application SSO spécifiée est supprimée d'un adaptateur. (Comme une application peut uniquement être affectée à un seul adaptateur, il n'est pas nécessaire de spécifier le nom de l'adaptateur.)  
  
### <a name="to-reset-notification"></a>Pour réinitialiser la notification  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops-réinitialiser \<nom de l’adaptateur &#124; tous les &#124; amortissement\>**  et appuyez sur ENTRÉE.  
  
     Cette commande efface le tableau d'amortissement et/ou les files d'attente de notification pour un seul adaptateur ou pour tous les adaptateurs, tel que spécifié. Le tableau d'amortissement stocke un historique de 10 minutes de modifications de mot de passe. Avant que le système de l'authentification unique de l'entreprise accepte ou envoie une modification de mot de passe, il vérifie le tableau d'amortissement pour voir s'il a effectué la même modification récemment. Si tel est le cas, la nouvelle modification est ignorée.  
  
### <a name="to-add-an-adapter-to-an-adapter-group"></a>Pour ajouter un adaptateur à un groupe d'adaptateurs  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops - addtogroup \<nom de l’adaptateur\> \<groupe d’adaptateurs\>**  et appuyez sur ENTRÉE.  
  
     Cette commande ajoute l'adaptateur spécifié au groupe d'adaptateurs spécifié. Alors qu'un adaptateur ne peut appartenir qu'à un seul groupe d'adaptateurs, un groupe d'adaptateurs peut contenir plusieurs adaptateurs.  
  
### <a name="to-delete-an-adapter-from-an-adapter-group"></a>Supprimer un adaptateur d'un groupe d'adaptateurs  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssops - deletefromgroup, \<nom de l’adaptateur\> \<groupe d’adaptateurs\>**  et appuyez sur ENTRÉE.  
  
     Cette commande supprime l'adaptateur spécifié du groupe d'adaptateurs spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation de mot de passe](../core/password-synchronization2.md)
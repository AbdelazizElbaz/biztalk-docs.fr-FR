---
title: Comment configurer la synchronisation de mot de passe MIIS ENTSSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89438935-37c1-4ac9-9ca2-7af8d9bfd3ae
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a1587c2e3c0d2164a7ffd3842b3d74df5b04685
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-entsso-for-miis-password-sync"></a>Configuration de l'authentification unique de l'entreprise (ENTSSO) pour la synchronisation de mot de passe à partir de MIIS
Après avoir configuré le fichier XML et MIIS (Microsoft Identity Integration Server), les étapes de configuration restantes se déroulent au sein du système d'authentification unique de l'entreprise (ENTSSO).  
  
### <a name="to-allow-password-sync-from-miis"></a>Pour autoriser la synchronisation de mot de passe à partir de MIIS  
  
1.  Dans Enterprise Single Sign-On, cliquez sur le **serveurs** nœud.  
  
2.  Cliquez sur le serveur approprié, puis cliquez sur **propriétés**.  
  
3.  Cliquez sur le **synchronisation de mot de passe** onglet.  
  
4.  Sélectionnez **autoriser la synchronisation du mot de passe à partir de MIIS**.  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-enable-password-sync-on-the-system-level"></a>Pour activer la synchronisation de mot de passe au niveau du système  
  
1.  Dans Enterprise Single Sign-On, cliquez sur le **système** nœud.  
  
2.  Cliquez sur **Propriétés**.  
  
     Le **propriétés** boîte de dialogue s’affiche.  
  
3.  Cliquez sur le **Options** onglet.  
  
4.  Dans le **activer la synchronisation de mot de passe** champ, sélectionnez **à partir de Windows vers les adaptateurs**.  
  
     **Configuration supplémentaire**  
  
     Pour terminer, vous devez configurer l'un des éléments suivants :  
  
    -   un adaptateur de synchronisation de mot de passe compatible avec la synchronisation des mots de passe Windows ;  
  
    -   la synchronisation de mot de passe directe activée sur au moins une application.  
  
     Pour plus d'informations sur la manière de procéder, consultez la documentation relative à la synchronisation de mot de passe.  
  
### <a name="to-configure-the-entsso-ma-for-miis-password-sync"></a>Pour configurer l'agent de gestion ENTSSO pour la synchronisation de mot de passe MIIS  
  
1.  Sur l’Agent de gestion ENTSSO **propriétés** , cliquez sur **configurer des Extensions**.  
  
2.  Dans le **les informations de connexion pour l’extension de mot de passe** , cliquez sur **paramètres**.  
  
3.  Dans le **Connect To** champ Entrez le nom de l’ordinateur qui reçoit les modifications de mot de passe.  
  
     Le format du nom de l'ordinateur doit être identique à celui utilisé lors de la création du nom principal de service (SPN) pour le service ENTSSO du domaine.  
  
     Exemple :  
  
     Format court - SPN = ENTSSO/ABCD1411, puis entrez ABCD1411  
  
4.  Format long - SPN = ENTSSO/ABCD1411.nom_entreprise.com, puis entrez ABCD1411.nom_entreprise.com  
  
### <a name="additional-configuration-steps"></a>Étapes de configuration supplémentaires  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Identity Integration Server**, puis cliquez sur **Identity Manager**.  
  
2.  Dans le menu **Outils** , cliquez sur **Options**.  
  
3.  Sélectionnez **activer la synchronisation de mot de passe**.  
  
4.  Dans le **afficher les Agents de gestion**, sélectionnez **ADMA**.  
  
5.  Dans le **Action** volet, sélectionnez **propriétés**.  
  
6.  Sur le **propriétés** page, sélectionnez **configurer des Partitions d’annuaire**, puis sélectionnez **activer cette partition comme source de synchronisation de mot de passe**.  
  
7.  Cliquez sur **cibles**, puis sélectionnez ENTSSOMA2 pour lui permettre de recevoir les modifications de mot de passe à partir de MIIS. Désactivez ENTSSOMA. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
8.  Dans le **Agent de gestion** afficher, sélectionnez **ENTSSOMA2**. Dans le volet droit, sélectionnez **propriétés**. Sur le **propriétés** , cliquez sur **configurer des Extensions**.  
  
9. Vérifiez que **activer la gestion de mot de passe** est sélectionné, puis cliquez sur **paramètres**.  
  
10. Dans le **paramètres de connexion** boîte de dialogue, spécifiez les éléments suivants :  
  
    -   Se connecter à : INTSVR1.fabrikam.com  
  
    -   Utilisateur : fabrikam\ssosvcact  
  
    -   Mot de passe : ssosvcact  
  
        > [!NOTE]
        >  Ce compte doit correspondre à celui du service ENTSSO configuré sur INTSVR1.fabrikam.com.  
  
11. Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.  
  
12. Vous pouvez également désactiver la synchronisation de mot de passe pour MIIS. Pour ce faire, dans **Identity Manager**, cliquez sur le **outils** menu, cliquez sur **Options**, puis désélectionnez **activer la synchronisation de mot de passe**.  
  
     Les restrictions suivantes seront applique :  
  
    -   Pour que la synchronisation de mot de passe fonctionne correctement, le nom principal de service doit être configuré sur le compte du service ENTSSO avec lequel l'agent de gestion ENTSSO communique.  
  
    -   Les communications entre MIIS et le serveur ENTSSO requièrent Kerberos.  
  
13. Lors de la configuration de l'extension de mot de passe dans la configuration de la connexion MIIS pour l'agent de gestion ENTSSO, le compte spécifié doit correspondre au compte de service du serveur ENTSSO qui reçoit les mots de passe en provenance de MIIS.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de l’Agent de gestion ENTSSO](../core/how-to-use-the-entsso-management-agent.md)
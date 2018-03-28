---
title: Activer la Validation des Codes d’identificateur Bank | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Bank Identifier Code (BIC), enabling
ms.assetid: d268a892-f304-44cb-b590-28ef359c8d99
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3868906d4f61242b1344a02147e4e71307d67d3
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="enabling-validation-of-bank-identifier-codes"></a>Activer la Validation des Codes d’identificateur de banque
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] schémas de vous assurer que les Codes d’identificateur de banque (BICs) spécifiée dans le document d’échange SWIFT respectent le format de données définis par le SWIFT de BIC. A4SWIFT prend également en charge la validation des BICs par rapport à une liste BIC spécifié par le client dans une base de données.  
  
 Vous pouvez effectuer cette validation si vous avez activé la validation de BRE et puis activé la validation BIC.  
  
 Par défaut, le programme d’installation A4SWIFT désactive la validation de BRE. Pour l’activer, vous devez définir le paramètre de configuration de la validation BRE sur true pour un pipeline de réception qui utilise le désassembleur A4SWIFT. Vous devez également exécuter l’utilitaire de déploiement BRE pour déployer la stratégie principal et la stratégie de validation spécifique au message de validation (MT*xxx*_Master_policy.xml et MT*xxx*_Validation_Policy.xml). Pour plus d’informations, consultez [fonctionne avec les stratégies BRE](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md) et [BRE, les règles de déploiement](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).  
  
 Une fois que vous avez activé la validation BRE, vous devez utiliser publier et déployer les deux stratégies de validation BIC (BIC_Master_Policy.xml et BIC_Validation_Policy.xml) à l’aide de l’Assistant Déploiement du moteur de règles. Avant cela, vous devez procédez comme suit :  
  
-   Remplir la base de données avec les valeurs BIC de SWIFT. Vous pouvez utiliser la table Bicplus dans la base de données A4SWIFT, qui est installé par le programme d’installation A4SWIFT, ou vous pouvez utiliser votre propre base de données personnalisée. Pour plus d’informations, consultez [la gestion de la Table dans la base de données A4SWIFT Bicplus](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md).  
  
-   Définir la base de données BIC et activer la validation BIC en personnalisant la stratégie BIC principale. Consultez la procédure ci-dessous.  
  
 Pour de meilleures performances, vous ne devez pas déployer les stratégies de validation BIC si la validation BIC n’est pas nécessaire.  
  
> [!NOTE]
>  Vous pouvez publier et déployer la stratégie de validation BIC uniquement si vous avez publié les vocabulaires A4SWIFT_Codelist et A4SWIFT_Functions. Publier ces vocabulaires en exécutant l’utilitaire de déploiement du moteur BRE sur l’assembly SWIFTSchemas. Pour plus d’informations, consultez [leçon 1 : déployer les règles d’entreprise connexes](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md).  
  
### <a name="to-customize-the-bic-master-policy"></a>Pour personnaliser la stratégie BIC principale  
  
1.  Ouvrez un éditeur XML (tel que bloc-notes) et accédez à  **< *lecteur*programme Files\Microsoft Microsoft BizTalk Accelerator pour SWIFT \<version\> Messages\ Pack\SWIFT de Message A4SWIFT-SRG\<version\>\Base stratégies**.  
  
2.  Ouvrez **BIC_Master_Policy.xml**. Remplacez les chaînes d’existants suivants avec les nouvelles valeurs.  
  
    > [!NOTE]
    >  Vous devez entrer des valeurs pour la table Bicplus dans la base de données A4SWIFT ou votre propre base de données personnalisée. La base de données A4SWIFT n’est pas la valeur par défaut dans BIC_Master_Policy.xml.  
  
    > [!NOTE]
    >  Les chaînes suivantes ne doivent pas figurer entre guillemets doubles.  
  
    |Chaîne existante|Remplacer par|  
    |---------------------|------------------|  
    |**SPÉCIFIEZ LE NOM DU SERVEUR SQL**|Le nom de la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] contenant la base de données contenant le code BIC.|  
    |**SPÉCIFIEZ LE NOM DE BASE DE DONNÉES BIC**|Le nom de la base de données qui contient la table BIC.|  
    |**SPÉCIFIEZ LA VALEUR DE LA SÉCURITÉ INTÉGRÉE**|**SSPI**|  
  
3.  Enregistrer la stratégie modifiée de Master.  
  
4.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Assistant Déploiement du moteur des règles métier**.  
  
5.  Dans la page d’accueil, cliquez sur **suivant**.  
  
6.  Dans la page de la tâche de déploiement, cliquez sur **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.  
  
7.  Dans la page magasin de stratégies, dans **nom SQL Server**, sélectionnez le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] qui contient vos bases de données BizTalk. Dans **base de données de Configuration sur le serveur sélectionné**, sélectionnez **BizTalkRuleEngineDb**, puis cliquez sur **suivant**.  
  
8.  Dans la page de fichier du moteur de règles d’importation stratégie/vocabulaire, accédez à  **< *lecteur*\Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Pack\SWIFT de Message Messages\A4SWIFT-SRG\<version\>\Base stratégies**, cliquez sur **BIC_Master_Policy.xml**, cliquez sur **ouvrez**, puis cliquez sur **Suivant**.  
  
9. Dans la page prêt, vérifier les données, puis cliquez sur **suivant**.  
  
10. Dans la page de l’importation de la stratégie/le vocabulaire, vérifiez que la commande a réussi, puis cliquez sur **suivant**.  
  
11. Sur la fin de la page de l’Assistant de déploiement du moteur de règles, cliquez sur **réexécuter cet Assistant**, puis cliquez sur **Terminer**.  
  
12. Dans la page d’accueil, cliquez sur **suivant**.  
  
13. Dans la page de la tâche de déploiement, cliquez sur **déployer la stratégie de**, puis cliquez sur **suivant**.  
  
14. Sur le **magasin de stratégies** page **nom SQL Server**, sélectionnez le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] qui contient vos bases de données BizTalk. Dans **base de données de Configuration sur le serveur sélectionné**, sélectionnez **BizTalkRuleEngineDb**, puis cliquez sur **suivant**.  
  
15. Sur le **déployer la stratégie de** page, sélectionnez **BIC_Master_Policy.1.0**, puis cliquez sur **suivant**.  
  
16. Sur le **prêt** , cliquez sur **suivant**.  
  
17. Dans la page déploiement de la stratégie, si le déploiement a réussi, cliquez sur **suivant**. Cliquez sur **réexécuter cet Assistant**, puis cliquez sur **Terminer**.  
  
18. Répétez les étapes 5 à 17 pour **BIC_Validation_Policy.xml**, saisie **BIC_Validation_Policy** au lieu de **BIC_Master_Policy**.  
  
19. Quittez l’Assistant Déploiement du moteur de règles.  
  
20. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**. Vérifiez que le **stratégies** liste inclut **BIC_Master_Policy** et **BIC_Validation_Policy** sous **stratégies**.  
  
21. Développez **Version 1.0 déployée** sous **BIC_Master_Policy**, puis cliquez sur **BIC_Master_Rule**.  
  
22. Dans le volet THEN, vérifiez que les propriétés de connexion SQL répertoriées sont correctes.  
  
    > [!NOTE]
    >  A4SWIFT ne récupère pas les modifications apportées à la stratégie de validation BIC principal jusqu'à ce que vous redémarrez le service BizTalk qui héberge le pipeline de réception qui est actuellement configuré pour utiliser le désassembleur SWIFT. A4SWIFT valide tous les documents qui passent par ce pipeline pour les valeurs BIC qui figurent dans la colonne BIC spécifiée dans la stratégie maître BIC. Le compte d’utilisateur utilisé pour démarrer ce service BizTalk (BTSNTSvc.exe) doit avoir accès à la base de données BIC et la table. Pour une meilleure sécurité, il est recommandé d’accorder l’accès en lecture seule à la base de données BIC et la table.  
  
    > [!NOTE]
    >  Si vous utilisez Message Repair et New Submission, le service de publication World Wide Web doit être redémarré (en exécutant iisreset.exe) pour la validation BIC travailler à partir d’InfoPath.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des stratégies BRE](../../adapters-and-accelerators/accelerator-swift/working-with-bre-policies.md)   
 [Gestion de la table Bicplus dans la base de données A4SWIFT](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)
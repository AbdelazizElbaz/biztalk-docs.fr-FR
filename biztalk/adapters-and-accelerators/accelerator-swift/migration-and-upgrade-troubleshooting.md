---
title: "Résolution des problèmes de mise à niveau et de migration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading, troubleshooting
- troubleshooting, upgrading
- troubleshooting, migrating
- migrating, troubleshooting
ms.assetid: 6e6c0ff9-7897-4de6-9e9b-b502b3a1785b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0e2a18b1cdba47c999150b5bc52c0b016aec61
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="migration-and-upgrade-troubleshooting"></a>Migration et la résolution des problèmes de mise à niveau
## <a name="assemblies-need-to-be-undeployed-before-an-upgrade"></a>Les assemblys doivent être annulé avant une mise à niveau  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez de mettre à niveau d’A4SWIFT, le processus de mise à niveau échoue.  
  
### <a name="possible-cause"></a>Cause possible  
 Les assemblys A4SWIFT suivants sont toujours déployés lors de la mise à niveau est effectuée : Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration, Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas, Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.  
  
> [!NOTE]
>  Il est inutile de redéployer Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas. Le programme d’installation redéploie cet assembly.  
  
### <a name="solution"></a>Solution  
 Annuler le déploiement manuellement les quatre assemblys A4SWIFT dans l’ordre suivant :  
  
-   Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration  
  
-   Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas  
  
-   Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.  
  
 Une fois que vous avez mis à niveau, redéployer ces assemblys (à l’aide de **BTSTask.exe**) dans l’ordre inverse.  
  
## <a name="an-upgrade-removes-access-permissions-for-the-service-folder"></a>Une mise à niveau supprime les autorisations d’accès pour le dossier du Service  
  
### <a name="symptom"></a>Symptôme  
 Après une mise à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], l’autorisation d’accès pour le BizTalk Accelerator pour SWIFT\Service dossier %programfiles%\Microsoft est incorrecte.  
  
### <a name="possible-cause"></a>Cause possible  
 Lorsque vous mettez à niveau vers [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], le processus de mise à niveau supprime les autorisations d’accès pour les groupes administrateurs d’A4SWIFT et les utilisateurs d’A4SWIFT de BizTalk Accelerator pour SWIFT\Service dossier %programfiles%\Microsoft.  
  
### <a name="solution"></a>Solution  
 Si vous rencontrez ce problème, définir manuellement les autorisations d’accès suivants pour le dossier du Service :  
  
|Groupe ou nom d'utilisateur|Autorisation|  
|------------------------|----------------|  
|Administrateurs d’A4SWIFT|Contrôle total|  
|Utilisateurs d’A4SWIFT|Lire et exécuter|  
  
 Pour définir ces autorisations, procédez comme suit :  
  
 Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à *% ProgramFiles%*\Microsoft BizTalk Accelerator pour SWIFT\Service.  
  
1.  Cliquez sur le dossier du Service, cliquez sur **propriétés**, puis cliquez sur le **sécurité** onglet.  
  
2.  Dans le volet de noms utilisateur ou de groupe, de la boîte de dialogue Propriétés du Service, cliquez sur **ajouter**, entrez   ***\<nom du serveur\>*\A4SWIFT administrateurs**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si le groupe d’administrateurs d’A4SWIFT est un groupe de domaine, entrez   ***\<nom de domaine\>*\A4SWIFT administrateurs**.  
  
3.  Répétez l’étape 2 pour   ***\<nom du serveur\>*\A4SWIFT utilisateurs**, ou  **\<* nom de domaine* \>\A4SWIFT utilisateurs ** si le groupe utilisateurs d’A4SWIFT est un groupe de domaine.  
  
4.  Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT administrateurs**. Dans le volet d’autorisations, sélectionnez **autoriser** pour **contrôle total**.  
  
5.  Dans le volet noms d’utilisateur ou de groupe, sélectionnez **A4SWIFT utilisateurs**. Dans le volet d’autorisations, cliquez sur **autoriser** pour **lire & exécuter**, **contenu du dossier**, et **en lecture**.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage : problèmes et résolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)
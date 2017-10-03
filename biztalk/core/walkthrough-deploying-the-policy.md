---
title: "Procédure pas à pas : Déploiement de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 205760e2-9cd4-496f-93cd-0f93bc5d3231
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00c603a3a0c52d735441858af6a2f602c30d1f51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-deploying-the-policy"></a>Procédure pas à pas : Déploiement de la stratégie
Cette procédure pas à pas fournit des instructions détaillées pour déployer le **ProcessPurchaseOrder** stratégie de trois manières suivantes :  
  
-   en exportant et important la stratégie à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise ;  
  
-   en exportant la stratégie dans un fichier XML et en l'important d'un fichier XML par l'intermédiaire de la console Administration de BizTalk Server ;  
  
-   en exportant la stratégie en tant que partie d'un fichier MSI et en important le fichier MSI par l'intermédiaire de la console Administration de BizTalk Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : exécution de la stratégie de suivi](../core/walkthrough-tracking-policy-execution.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette rubrique contient les trois procédures pas à pas suivantes :  
  
1.  La première procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise. Le tableau ci-dessous décrit en détail les procédures internes qu'elle contient.  
  
    |Titre de la procédure|Description de la procédure|  
    |---------------------|---------------------------|  
    |Pour exporter POVocabulary 1.0 et 1.1 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise|Fournit des instructions détaillées pour l’exportation des versions 1.0 et 1.1 de la **POVocabulary** vocabulaire XML des fichiers à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise.|  
    |Pour exporter ProcessPurchaseOrder 1.3 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise|Fournit des instructions détaillées pour l’exportation de la version 1.3 de la **ProcessPurchaseOrder** stratégie vers un fichier XML à l’aide de l’Assistant de déploiement de moteur de règles d’entreprise.|  
    |Pour supprimer ProcessPurchaseOrder et POVocabulary|Fournit des instructions détaillées pour la suppression de la **ProcessPurchaseOrder** stratégie et **POVocabulary** vocabulaire afin que vous puissiez tester l’importation du XML des fichiers pour recréer ces derniers.|  
    |Pour importer POVocabulary 1.0 et 1.1 depuis un fichier XML et les recréer|Fournit des instructions détaillées pour l’importation du fichier de vocabulaire XML que vous avez créé dans la première procédure pour recréer le **POVocabulary** vocabulaire.|  
    |Pour vérifier que POVocabulary 1.0 et 1.1 ont été recréés|Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que les versions 1.0 et 1.1 de **POVocabulary** sont recréés.|  
    |Pour importer ProcessPurchaseOrder 1.3 depuis un fichier XML et la recréer|Fournit des instructions détaillées pour l’importation du fichier XML de stratégie que vous avez créé dans la deuxième procédure pour recréer la version 1.3 de la **ProcessPurchaseOrder** stratégie.|  
    |Pour vérifier que ProcessPurchaseOrder 1.3 a été recréée|Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que la version 1.3 de la **ProcessPurchaseOrder** stratégie est recréée.|  
  
2.  La deuxième procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide d’un fichier XML exporté à partir de la console Administration de BizTalk Server suit tableau décrit les procédures dans cette procédure pas à pas.  
  
    |Titre de la procédure|Description de la procédure|  
    |---------------------|---------------------------|  
    |Pour exporter la stratégie ProcessPurchaseOrder 1.3 et le vocabulaire POVocabulary dans un fichier XML|Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour exporter les **ProcessPurchaseOrder** stratégie et le **POVocabulary** le vocabulaire vers un fichier XML.|  
    |Pour supprimer la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour la suppression de la **ProcessPurchaseOrder** stratégie à partir de **RuleTestApp** et la base de données du moteur de règles.|  
    |Pour importer le fichier XML afin de recréer la stratégie ProcessPurchaseOrder|Fournit des instructions détaillées pour l’importation du fichier XML que vous avez exporté dans la première procédure pour recréer le **ProcessPurchaseOrder** stratégie.|  
    |Pour ajouter la stratégie ProcessPurchaseOrder à l'application RuleTestApp|Fournit des instructions détaillées pour l’ajout du **ProcessPurchaseOrder** stratégie pour le **RuleTestApp** application.|  
  
3.  La troisième procédure contient les procédures de déploiement de la **ProcessPurchaseOrder** stratégie à l’aide d’un fichier MSI exporté à partir de la console Administration de BizTalk Server. Le tableau ci-dessous décrit en détail les procédures internes qu'elle contient.  
  
    |Titre de la procédure|La procédure contient des instructions détaillées correspondant à l'objectif suivant :|  
    |---------------------|---------------------------------------------------|  
    |Pour exporter l'application RuleTestApp dans un fichier MSI|Fournit des instructions détaillées pour l’exportation de la **RuleTestApp** application dans un fichier MSI, qui est utilisée ultérieurement pour recréer l’application.|  
    |Pour supprimer l'application RuleTestApp|Fournit des instructions détaillées pour la suppression de la **RuleTestApp** application afin que vous puissiez tester recréer l’application à l’aide du fichier MSI.|  
    |Pour vérifier la suppression de la stratégie ProcessPurchaseOrder et du vocabulaire POVocabulary|Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que le **ProcessPurchaseOrder** stratégie et vocabulaire POVocabulary sont supprimés.|  
    |Pour importer le fichier MSI afin de recréer l'application RuleTestApp|Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour importer le fichier MSI pour recréer le **RuleTestApp** application.|  
    |Pour vérifier l'ajout de la stratégie ProcessPurchaseOrder à l'application RuleTestApp|Fournit des instructions détaillées pour l’utilisation de la console Administration de BizTalk Server pour vérifier que le **ProcessPurchaseOrder** stratégie est ajoutée à la **RuleTestApp** application.|  
    |Pour vérifier que la stratégie ProcessPurchaseOrder et le vocabulaire POVocabulary ont été recréés|Fournit des instructions détaillées pour l’utilisation de l’éditeur des règles d’entreprise pour vérifier que le **ProcessPurchaseOrder** stratégie et **POVocabulary** vocabulaire sont recréées.|  
    |Pour tester la solution|Fournit des instructions pas à pas pour le test de la solution.|  
  
## <a name="procedures-for-deploying-the-processpurchaseorder-policy-by-using-the-business-rules-engine-deployment-wizard"></a>Procédures de déploiement de la stratégie ProcessPurchaseOrder à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise  
  
#### <a name="to-export-povocabulary-10-and-11-by-using-the-business-rules-engine-deployment-wizard"></a>Pour exporter POVocabulary 1.0 et 1.1 à l'aide de l'Assistant Déploiement du Moteur des règles d'entreprise  
  
1.  Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Cliquez sur **Suivant**.  
  
3.  Sur le **la tâche de déploiement** page, sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données**, puis cliquez sur **suivant**.  
  
4.  Sur le **magasin de stratégies** , cliquez sur **suivant**.  
  
5.  Sur le **Exporter stratégie/vocabulaire** , cliquez sur **vocabulaire**.  
  
6.  Sélectionnez **povocabulary 1.0** dans la liste déroulante pour **stratégie/le vocabulaire**, tapez ou cliquez sur Parcourir pour spécifier le nom de fichier de sortie XML en tant que **C:\BRE-walkthroughs\POVocabulary10.xml**, puis cliquez sur **suivant**.  
  
7.  Sur le **prêt** , cliquez sur **suivant**.  
  
8.  Sur le **Exporter stratégie/vocabulaire** , cliquez sur **suivant.**  
  
9. Sélectionnez **réexécuter cet Assistant**, puis cliquez sur **Terminer**.  
  
     Étant donné que vous avez sélectionné **réexécuter cet Assistant**, le premier écran de l’Assistant s’affiche à nouveau.  
  
10. Répétez les étapes 2 à 6.  
  
11. Sélectionnez **povocabulary 1.1** dans la liste déroulante pour **stratégie/le vocabulaire**, tapez ou cliquez sur Parcourir pour spécifier le nom de fichier de sortie XML en tant que **C:\BRE-walkthroughs\POVocabulary11.xml**, puis cliquez sur **suivant**.  
  
12. Répétez les étapes 8 et 9.  
  
13. Cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Vous devez exporter les versions 1.0 et 1.1 de **POVocabulary** car **ProcessPurchaseOrder** 1.3 repose sur les deux versions de **POVocabulary**. Le **nombre maximal d’éléments autorisés** définition est utilisée à partir de la version 1.1 du vocabulaire. Le **quantité requise** et **état de la demande** définitions sont utilisées à partir de la version 1.0.  
  
#### <a name="to-export-processpurchaseorder-13-by-using-the-business-rule-engine-deployment-wizard"></a>Pour exporter ProcessPurchaseOrder 1.3 à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise  
  
1.  Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles** , cliquez sur **suivant**.  
  
3.  Sélectionnez **Exporter stratégie/vocabulaire vers le fichier à partir de la base de données**, puis cliquez sur **suivant**.  
  
4.  Sur le **magasin de stratégies** , cliquez sur **suivant**.  
  
5.  Vérifiez que le **stratégie** option est sélectionnée.  
  
6.  Sélectionnez **ProcessPurchaseOrder.1.3** dans la liste déroulante pour **stratégie/le vocabulaire**.  
  
7.  Tapez ou cliquez sur Parcourir pour spécifier **C:\BRE-walkthroughs\ProcessPOPolicy13.xml** comme nom de fichier de sortie XML.  
  
8.  Cliquez sur **suivant** trois reprises, puis cliquez sur **Terminer**.  
  
#### <a name="to-delete-processpurchaseorder-and-povocabulary"></a>Pour supprimer ProcessPurchaseOrder et POVocabulary  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez Éditeur des règles d’entreprise déjà ouvrir, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **supprimer**. Si **supprimer** est désactivé, cliquez sur **Version 1.0**, puis cliquez sur **annuler le déploiement**.  
  
    > [!NOTE]
    >  Les versions de la stratégie déployée ne peuvent être supprimées. Vous devez annuler le déploiement d'une stratégie avant de pouvoir en supprimer une version.  
  
3.  Cliquez sur **Oui** dans la boîte de message de confirmation.  
  
4.  Répétez les étapes 2 et 3 pour supprimer **Version 1.1**.  
  
5.  Répétez les étapes 2 et 3 pour supprimer **Version 1.2**.  
  
6.  Avec le bouton droit **Version 1.3 déployée**, puis cliquez sur **annuler le déploiement**. Si le **annuler le déploiement** option est désactivée, vous pouvez ignorer cette étape.  
  
7.  Dans la fenêtre Explorateur de faits, développez **vocabulaires**, avec le bouton droit **POVocabulary**, puis cliquez sur **supprimer**.  
  
#### <a name="to-import-from-xml-to-re-create-povocabulary-10-and-11"></a>Pour importer POVocabulary 1.0 et 1.1 depuis un fichier XML et les recréer  
  
1.  Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles**, cliquez sur **suivant**.  
  
3.  Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.  
  
4.  Sur le **magasin de stratégies** , cliquez sur **suivant**.  
  
5.  Rechercher et sélectionner le **POVocabulary10.xml** fichier que vous avez créé dans la première procédure.  
  
6.  Cliquez sur **ouvrir** ou double-cliquez sur **POVocabulary10.xml**.  
  
7.  Cliquez sur **suivant** dans l’Assistant Déploiement du moteur des règles.  
  
8.  Cliquez sur **Suivant**.  
  
9. Cliquez sur **Suivant**.  
  
10. Sélectionnez **réexécuter cet Assistant**, puis cliquez sur **Terminer**.  
  
11. Répétez les étapes 2 à 9 pour importer **POVocabulary11.xml**.  
  
12. Cliquez sur **Terminer**.  
  
#### <a name="to-verify-that-povocabulary-10-and-11-are-re-created"></a>Pour vérifier que POVocabulary 1.0 et 1.1 ont été recréés  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez déjà ouvert, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet.  
  
3.  Développez **vocabulaires**, et vous devez voir **POVocabulary**.  
  
4.  Développez **POVocabulary**, et vous devez voir **Version 1.0** et **Version 1.1**.  
  
#### <a name="to-import-from-xml-to-re-create-processpurchaseorder-13"></a>Pour importer ProcessPurchaseOrder 1.3 depuis un fichier XML et la recréer  
  
1.  Sur le **Démarrer** menu, ouvrir **Assistant de déploiement du moteur de règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Sur le **Bienvenue dans l’Assistant Déploiement du moteur de règles**, cliquez sur **suivant**.  
  
3.  Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/le vocabulaire à base de données de base de données fichierPour à partir du fichier**, puis cliquez sur **suivant**.  
  
4.  Sur le **magasin de stratégies** , cliquez sur **suivant**.  
  
5.  Rechercher et sélectionner le **ProcessPOPolicy13.xml** fichier que vous avez créé précédemment dans cette procédure pas à pas.  
  
6.  Cliquez sur **ouvrir** ou double-cliquez sur **ProcessPOPolicy13.xml**.  
  
7.  Cliquez sur **suivant** dans l’Assistant Déploiement du moteur des règles.  
  
8.  Cliquez sur **Suivant**.  
  
9. Cliquez sur **Suivant**, puis sur **Terminer**.  
  
#### <a name="to-verify-that-processpurchaseorder-13-is-re-created"></a>Pour vérifier que ProcessPurchaseOrder 1.3 a été recréée  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez déjà ouvert, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies** et vous devez voir **ProcessPurchaseOrder**.  
  
3.  Développez **ProcessPurchaseOrder** et vous devez voir **Version 1.3 publiée**.  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-xml-file-exported-from-the-biztalk-server-administration-console"></a>Procédures de déploiement de la stratégie à l'aide d'un fichier XML exporté depuis la console Administration de BizTalk Server  
  
#### <a name="to-export-the-processpurchaseorder-13-policy-and-the-povocabulary-vocabulary-to-an-xml-file"></a>Pour exporter la stratégie ProcessPurchaseOrder 1.3 et le vocabulaire POVocabulary dans un fichier XML  
  
1.  Sur le **Démarrer** menu, ouvrez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]. Si l'outil est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
2.  Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez **RuleTestApp** .  
  
3.  Cliquez sur **stratégies** et assurez-vous que la stratégie ProcessPurchaseOrder 1.3 dans la liste.  
  
4.  Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **exporter**.  
  
5.  Dans le **exporter les stratégies** boîte de dialogue zone, assurez-vous que le **ProcessPurchaseOrder** stratégie et le **POVocabulary** sont sélectionnés.  
  
    > [!NOTE]
    >  Vous pouvez exporter toutes les stratégies dans une application dans un fichier XML en cliquant sur **RuleTest** , puis en cliquant sur **exporter** sur la **stratégies** menu. Cela vous permet d'exporter l'ensemble des stratégies et le vocabulaire utilisés par cette application dans un fichier XML unique.  
  
    > [!NOTE]
    >  Vous pouvez exporter toutes les stratégies dans toutes les applications dans un fichier XML en cliquant sur le **Applications** nœud, puis cliquez sur **exporter** sur la **stratégies** menu. Cela vous permet d'exporter l'ensemble des stratégies et des vocabulaires utilisés par ces applications dans un fichier XML unique.  
  
6.  Spécifiez un nom de fichier de sortie XML (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**), puis cliquez sur **Ok**.  
  
#### <a name="to-delete-the-processpurchaseorder-policy"></a>Pour supprimer la stratégie ProcessPurchaseOrder  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **ProcessPurchaseOrder** dans la liste, puis cliquez sur **supprimer**.  
  
2.  Cliquez sur **Oui** dans les **supprimer la stratégie** boîte de message.  
  
    > [!NOTE]
    >  Si la stratégie affiche l'état déployé, il est impossible de la supprimer. Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **annuler le déploiement** pour annuler le déploiement de la stratégie. Le **supprimer** élément de menu est disponible lorsque la stratégie est annulée.  
  
    > [!NOTE]
    >  Les vocabulaires sur lesquels le **ProcessPurchaseOrder** dépend de la stratégie, dans ce cas **POVocabulary**, sont également supprimés.  
  
    > [!NOTE]
    >  Lorsque vous supprimez une stratégie d'une application, la stratégie et les vocabulaires sur lesquels elle repose sont supprimés de la base de données du moteur de règles et non uniquement de l'application.  
  
#### <a name="to-import-the-xml-file-to-re-create-the-processpurchaseorder-policy"></a>Pour importer le fichier XML afin de recréer la stratégie ProcessPurchaseOrder  
  
1.  Dans la console Administration de BizTalk Server, développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.  
  
2.  Avec le bouton droit **Applications**, pointez sur **importation**, puis cliquez sur **stratégies**.  
  
3.  Recherchez et double-cliquez sur le fichier XML (**C:\BRE-Walkthroughs\ProcessPOFromAdmin.xml**) que vous avez créé dans la première procédure.  
  
4.  Développez  **\<tous les artefacts >** sous **Applications**.  
  
5.  Cliquez sur **stratégies**, et vous devez voir la version 1.3 de la **ProcessPurchaseOrder** stratégie dans la liste.  
  
6.  Appuyez sur F5 pour actualiser la vue. Le **ProcessPurchaseOrder** stratégie doit être dans le **pas publiées** état.  
  
#### <a name="to-add-the-processpurchaseorder-policy-to-the-ruletestapp-application"></a>Pour ajouter la stratégie ProcessPurchaseOrder à l'application RuleTestApp  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **ProcessPurchaseOrder** stratégie, puis cliquez sur **publier**.  
  
    > [!NOTE]
    >  Seules les stratégies publiées peuvent être ajoutées à une application BizTalk.  
  
2.  Dans le **Applications** nœud, développez **RuleTestApp**.  
  
3.  Cliquez sur **stratégies** dans **RuleTestApp**.  
  
4.  Avec le bouton droit dans la liste de droite, pointez sur **ajouter**, puis cliquez sur **stratégie**.  
  
5.  Développez le **ProcessPurchaseOrder** nœud, sélectionnez la case à cocher **Version 1.3 (publiée)**, puis cliquez sur **OK**. .  
  
6.  Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **déployer**. Si vous ne voyez pas **ProcessPurchaseOrder** dans la liste, appuyez sur F5 pour actualiser l’affichage.  
  
7.  Cliquez sur **Oui** dans la boîte de message de confirmation.  
  
## <a name="procedures-for-deploying-the-policy-by-using-an-msi-file"></a>Procédures de déploiement de la stratégie à l'aide d'un fichier MSI  
  
#### <a name="to-export-the-ruletestapp-application-to-an-msi-file"></a>Pour exporter l'application RuleTestApp dans un fichier MSI  
  
1.  Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**. Si l'outil est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
2.  Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Avec le bouton droit **RuleTestApp**, pointez sur **exporter**, puis cliquez sur **fichier MSI**.  
  
4.  Sur le **Bienvenue dans l’Assistant Exportation de fichier MSI** , cliquez sur **suivant**.  
  
5.  Sur le **sélectionner les ressources** page, passez en revue toutes les options par défaut, puis cliquez sur **suivant**.  
  
6.  Sur le **spécifier les hôtes IIS** , cliquez sur **suivant**.  
  
7.  Sur le **dépendances** , cliquez sur **suivant**.  
  
8.  Sur le **Destination** , spécifiez le répertoire et le nom du fichier MSI **C:\BRE-Walkthroughs\RuleTestApp.msi**.  
  
9. Cliquez sur **Exporter**.  
  
10. Sur le **Résumé** , cliquez sur **Terminer**.  
  
    > [!NOTE]
    >  Lorsque vous exportez l'application RuleTestApp, les stratégies et vocabulaires qu'elle utilise sont également exportés dans le fichier MSI. Quand vous procéderez à l'importation du fichier MSI, le vocabulaire, l'application et l'application seront tous recréés.  
  
#### <a name="to-delete-the-ruletestapp-application"></a>Pour supprimer l'application RuleTestApp  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **RuleTestApp**et vérifiez si le **supprimer** menu est activé ou désactivé.  
  
2.  Si **supprimer** est désactivé, cliquez sur **RuleTestApp**, cliquez sur **arrêter**, sélectionnez **arrêt complet - arrêter l’Instance**, puis cliquez sur  **Arrêter**.  
  
3.  Avec le bouton droit **RuleTestApp**, puis cliquez sur **supprimer**.  
  
4.  Cliquez sur **Oui** pour confirmer la suppression.  
  
    > [!NOTE]
    >  Lorsque vous supprimez une application, toutes les stratégies qu'elle contient, ainsi que les vocabulaires qui lui sont associés, sont également supprimés de la base de données du moteur de règles.  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-deleted"></a>Pour vérifier la suppression de la stratégie ProcessPurchaseOrder et du vocabulaire POVocabulary  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez Éditeur des règles d’entreprise déjà ouvert, appuyez sur F5 pour actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**et assurez-vous que la stratégie ProcessPurchaseOrder n’existe pas.  
  
3.  Dans la fenêtre Explorateur de faits, développez **vocabulaires**et assurez-vous que POVocabulary n’existe pas.  
  
#### <a name="to-import-the-msi-file-to-re-create-the-ruletestapp-application"></a>Pour importer le fichier MSI afin de recréer l'application RuleTestApp  
  
1.  Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**. Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.  
  
2.  Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.  
  
3.  Avec le bouton droit **Applications**, pointez sur **importation**, puis cliquez sur **fichier MSI**.  
  
4.  Sur le **Bienvenue dans l’Assistant Importation de** page, recherchez et sélectionnez le fichier MSI (Ruletestapp) que vous avez exporté précédemment pour le **fichier MSI à importer** paramètre.  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **paramètres de l’Application** , cliquez sur **suivant**.  
  
7.  Sur le **paramètres d’environnement cible Application** , cliquez sur **suivant**.  
  
8.  Sur le **résumé d’importation** , cliquez sur **importation**.  
  
9. Sur le **importation réussie** , cliquez sur **Terminer**. Vous devez voir que la **RuleTestApp** application est créée sous **Applications** dans la console Administration de BizTalk Server.  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-is-added-to-ruletestapp"></a>Pour vérifier l'ajout de la stratégie ProcessPurchaseOrder à l'application RuleTestApp  
  
1.  Développez **RuleTestApp** dans la console Administration de BizTalk Server.  
  
2.  Sélectionnez **stratégies** et vous devez voir **ProcessPurchaseOrder** dans la liste dans le volet droit.  
  
#### <a name="to-verify-that-the-processpurchaseorder-policy-and-povocabulary-vocabulary-are-re-created"></a>Pour vérifier que la stratégie ProcessPurchaseOrder et le vocabulaire POVocabulary ont été recréés  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. S'il est déjà ouvert, appuyez sur F5 pour l'actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de stratégies, développez **stratégies**et vous assurer que **ProcessPurchaseOrder** existe.  
  
3.  Dans la fenêtre Explorateur de faits, développez **vocabulaires**et vous assurer que **POVocabulary** existe.  
  
#### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Sur le **Démarrer** menu, ouvrir **Administration de BizTalk Server**. Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.  
  
2.  Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**.  
  
4.  Cliquez sur **Démarrer**.  
  
5.  Copie **SamplePO.xml** que vous avez créé dans [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) dans le répertoire d’entrée pour l’orchestration.  
  
6.  Vous devez voir un fichier de sortie dans le répertoire de sortie de l'orchestration. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
7.  Répétez les étapes 3 et 4 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**XYZ**).  
  
## <a name="comments"></a>Commentaires  
  
-   Il s’agit de **très important** pour n’oubliez pas que lorsque vous supprimez une stratégie à partir d’une application, vous ne supprimez pas uniquement l’association entre l’application et la stratégie ; vous également supprimer la stratégie et son vocabulaire de la règle moteur de base de données.  
  
-   Lorsque vous démarrez une application, elle procède par défaut au déploiement automatique des stratégies. De même, lorsque vous arrêtez une application et sélectionnez **arrêt complet - arrêter les Instances**, les stratégies associées soient automatiquement annulés. Lorsque vous sélectionnez **arrêt partiel - Suspendre les instances en cours d’exécution**, les stratégies associées ne sont pas automatiquement annulés.  
  
-   Vous devez actualiser la vue de l'Éditeur des règles d'entreprise et de la console Administration de BizTalk Server pour vous assurer que vous avez devant vous les informations les plus récentes avant de procéder à la moindre opération.  
  
-   Si vous créez une nouvelle version d'une stratégie dont la version précédente est associée à une application BizTalk, vous devez ajouter manuellement la nouvelle version de la stratégie à l'application. Ne supprimez pas l'ancienne version de la stratégie, sauf si vous êtes sûr(e) de vouloir la supprimer du moteur de règles.  
  
-   Vous pouvez fusionner deux ou plusieurs fichiers XML BRL (Business Rule Language) dans un seul fichier BRL avant de procéder à l'importation Le code ci-après illustre trois fichiers BRL : Le premier fichier contient le **POVocabulary** vocabulaire. Le deuxième fichier BRL contient le **ProcessPurchaseOrder** stratégie. Le troisième fichier BRL contient à la fois le **POVocabulary** vocabulaire et **ProcessPurchaseOrder** stratégie. Ce dernier fichier est créé selon les étapes suivantes :  
  
    1.  Créer un nouveau fichier à l’aide de n’importe quel fichier éditeur et l’enregistrer dans un fichier XML (par exemple : POPolicyVocabulary.xml).  
  
    2.  Copiez l'intégralité du fichier XML depuis le fichier BRL file contenant le vocabulaire.  
  
    3.  Copiez le bloc de ruleset (commence par la \<ruleset > balise et se termine par le \</ruleset > balise) à partir de la deuxième fichier BRL.  
  
    4.  Enregistrez le nouveau fichier. Vous pouvez importer ce fichier XML unique pour créer le **POVocabulary** vocabulaire et **ProcessPurchaseOrder** stratégie.  
  
    > [!NOTE]
    >  L'ordre des nœuds du vocabulaire et de l'ensemble de règles dans le fichier BRL fusionné n'a pas d'importance. Le nœud de l'ensemble de règles peut se trouver avant le nœud du vocabulaire.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
    </brl>  
  
    <?xml version="1.0" encoding="utf-8"?>  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
  
    <brl  
    xmlns="http://schemas.microsoft.com/businessruleslanguage/2002">  
      <vocabulary id="e588676a-ba01-4f37-b59d-91f7e1eb1f1a" name="POVocabulary" uri="" description="">  
           ……   
      </vocabulary>  
      <ruleset name="ProcessPurchaseOrder">  
         ……  
      </ruleset>  
    </brl>  
    ```
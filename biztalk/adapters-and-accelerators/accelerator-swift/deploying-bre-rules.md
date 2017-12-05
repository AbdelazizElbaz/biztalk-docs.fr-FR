---
title: "Déployer des règles BRE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, BRE policies
- BRE policies, deploying
ms.assetid: 3a66aa57-e7f9-400f-963c-eda12fb1e659
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5627731bd84a761ffb62b95646876c768e3298ea
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-bre-rules"></a>MOTEUR des règles de déploiement
Vous devez déployer les règles BRE utilisées par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] orchestrations pour traiter les messages SWIFT.  
  
 **Résumé**  
  
 Publier les vocabulaires suivantes :  
  
-   Vocabulaires A4SWIFT_CodeLists.XML et A4SWIFT_Functions.xml. Ceux-ci sont situés dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\< version\>\Base Policies\Vocabulary. Publier et de les déployer à l’aide de l’utilitaire de déploiement du moteur BRE.  
  
 Publier et déployer des stratégies suivantes :  
  
-   Les stratégies de base SWIFT pour schéma de message, y compris SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml et des stratégies de règle de réseau (SWIFT_NetworkRulexxx_Policy.xml) pour déployées schémas. Ceux-ci sont situés dans \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base stratégies. Publier et de les déployer à l’aide de l’utilitaire de déploiement du moteur BRE.  
  
-   Principale et la validation des stratégies associées à déploiement des schémas de message (MTxxx_Master_Policy.xml et MTxxx_Validation_Policy.xml). Ceux-ci sont situés dans \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\ MTxxx. Publier et de les déployer à l’aide de l’utilitaire de déploiement du moteur BRE.  
  
-   Principale et la validation de stratégies associées à validation BIC (BIC_Master_Policy.xml et BIC_Validation_Policy.xml), si la validation de BIC est requise. Ceux-ci sont situés dans \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base stratégies. Avant la publication et le déploiement de ces stratégies, vous devez personnaliser BIC_Master_Policy.xml avec les noms de SQL Server, le nom de la base de données BIC et intégré de valeur de sécurité. Pour plus d’informations, consultez [l’activation de Validation d’identificateur de Codes de la banque](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md). Publier et de les déployer à l’aide de l’Assistant Déploiement du moteur de règles.  
  
### <a name="to-deploy-bre-rules"></a>Pour déployer des règles BRE  
  
1.  Exécutez l’utilitaire de déploiement du moteur BRE. Pour plus d’informations, consultez « Déploiement BRE règles tous les à une fois » ci-dessous. Cet utilitaire Publier et déployer les éléments suivants :  
  
    -   Vocabulaires A4SWIFT_CodeLists.XML et A4SWIFT_Functions.xml  
  
    -   Stratégies de base SWIFT pour le schéma du message, y compris SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml et des stratégies de règle de réseau (SWIFT_NetworkRulexxx_Policy.xml)  
  
    -   Principale et la validation des stratégies associées déploiement des schémas de message (MTxxx_Master_Policy.xml et MTxxx_Validation_Policy.xml)  
  
2.  Personnaliser BIC_Master_Policy.xml avec les noms de SQL server, la valeur de sécurité intégrée et nom de base de données BIC. Pour plus d’informations, consultez [l’activation de Validation d’identificateur de Codes de la banque](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).  
  
3.  Exécuter l’Assistant de déploiement du moteur de règles pour publier et déployer BIC_Master_Policy.xml et BIC_Validation_Policy.xml (dans \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base stratégies). Pour plus d’informations, consultez « Déploiement BRE règles un à un temps » ci-dessous.  
  
## <a name="tools-for-deploying-the-policies"></a>Outils pour déployer des stratégies  
 Il est le moyen le plus simple pour publier des vocabulaires et déployer les stratégies en utilisant l’utilitaire de déploiement du moteur de règles d’entreprise (BRE) dans le Kit de développement logiciel (SDK) A4SWIFT. Vous pouvez également le faire à l’aide de le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Assistant Déploiement du moteur de règles qui effectue la même vocabulaire d’une tâche ou d’une stratégie à la fois.  
  
> [!NOTE]
>  L’utilitaire de déploiement du moteur BRE ne déploie pas les stratégies de Master BIC et Validation BIC. Vous devez déployer à l’aide de l’Assistant Déploiement du moteur de règles.  
  
### <a name="deploying-bre-rules-all-at-once"></a>Déploiement de règles du moteur BRE tous en même temps  
 L’utilitaire de déploiement du moteur de règles d’entreprise (BRE) effectue une série de tâches de publication et de déploiement en une seule étape. Vous devez exécuter à nouveau l’utilitaire de déploiement chaque fois que vous ajoutez un schéma à votre projet.  
  
##### <a name="to-deploy-bre-rules-using-the-bre-deployment-utility"></a>Pour déployer des règles BRE à l’aide de l’utilitaire de déploiement du moteur BRE  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **del’utilitairededéploiementBRE**.  
  
2.  Dans la boîte de dialogue Utilitaire de déploiement du moteur BRE, cliquez sur **Parcourir**.  
  
3.  Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez l’assembly de projet que vous avez déployé dans [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md), puis cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue Utilitaire de déploiement du moteur BRE, cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Selon les schémas que vous avez déployé avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE. Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant :  
  
    > [!NOTE]
    >  « Déploiement s’est terminée. Afficher le fichier journal ou l’éditeur des règles d’entreprise pour plus d’informations. »  
  
5.  Fermez la boîte de dialogue Utilitaire de déploiement du moteur BRE.  
  
6.  Ouvrez [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer. Accédez à \< *lecteur*\>: \Documents and Settings\All Users\Application données et vérifiez que le fichier journal BREDeploymentLog.txt apparaît dans ce lecteur.  
  
7.  Redémarrez le Service de mise à jour de moteur de règle. En cliquant sur **Démarrer**, puis sur **exécuter**, saisie **services.msc**, puis en cliquant sur **OK**. Dans le **Services (Local)** fenêtre, avec le bouton droit **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.  
  
### <a name="deploying-bre-rules-one-at-a-time"></a>Déploiement de règles du moteur BRE une à la fois  
 Vous pouvez utiliser l’Assistant Déploiement du moteur de règles à publier des vocabulaires et déployer des stratégies d’un à la fois. Pour un vocabulaire, ce processus implique l’importation et la publication du vocabulaire pour la base de données à partir d’un fichier en une seule étape. Pour une stratégie, le processus implique l’importation et la publication de la stratégie en une seule étape et son déploiement dans une autre étape.  
  
##### <a name="to-deploy-bre-rules-using-the-rules-engine-deployment-wizard"></a>Pour déployer des règles BRE à l’aide de l’Assistant Déploiement du moteur de règles  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Assistant Déploiement du moteur des règles métier**.  
  
2.  Dans la page d’accueil de l’Assistant de déploiement du moteur de règles, cliquez sur **suivant**.  
  
3.  Dans la page de la tâche de déploiement, cliquez sur **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.  
  
4.  Dans la page magasin de stratégies, dans le **liste nom du serveur SQL**, sélectionnez votre serveur, puis, dans le **base de données de Configuration sur le serveur sélectionné** liste, sélectionnez **BizTalkRuleEngineDb**. Cliquez sur **Suivant**.  
  
5.  Dans la page de fichier du moteur de règles d’importation stratégie/vocabulaire, cliquez sur **Parcourir**.  
  
6.  Sur la stratégie d’importation à partir de la page de fichier, dans le **Regarder dans** liste déroulante, accédez à un des dossiers suivants, en fonction de la stratégie ou de vocabulaire :  
  
    -   \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies\Vocabulary pour A4SWIFT_ CodeLists.xml et A4SWIFT_Functions.xml  
  
    -   \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base SWIFT_Reference_Policy.xml, des stratégies SWIFT_PartyIdentifier_Policy.XML, les stratégies de règles de réseau, BIC_Master_Policy.xml et BIC_Validation_Policy.xml  
  
    -   \<lecteur\>: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MTxxx pour le masque et la validation stratégies associées aux schémas de message déployé  
  
7.  Sélectionnez la stratégie que vous souhaitez déployer, puis cliquez sur **ouvrir**.  
  
8.  Dans la page de fichier du moteur de règles d’importation stratégie/vocabulaire, cliquez sur **suivant**.  
  
9. Dans la page prêt, cliquez sur **suivant**.  
  
10. Dans la page de l’importation de la stratégie/le vocabulaire, vérifiez que la commande a réussi, puis cliquez sur **suivant**.  
  
11. Si vous souhaitez déployer une stratégie, dans la page Fin de la page de l’Assistant de déploiement du moteur de règles, cliquez sur **réexécuter cet Assistant**, puis cliquez sur **Terminer**.  
  
12. Dans la page d’accueil de l’Assistant de déploiement du moteur de règles, cliquez sur **suivant**.  
  
13. Dans la page de la tâche de déploiement, cliquez sur **déployer la stratégie de**, puis cliquez sur **suivant**.  
  
14. Dans la page magasin de stratégies, dans le **liste nom du serveur SQL**, sélectionnez votre serveur, puis, dans le **base de données de Configuration sur le serveur sélectionné** liste, sélectionnez **BizTalkRuleEngineDb**. Cliquez sur **Suivant**.  
  
15. Dans la page déployer la stratégie, cliquez sur la flèche vers le bas en regard du **stratégie du moteur de règles** zone de texte, sélectionnez la stratégie que vous venez de publier, puis cliquez sur **suivant**.  
  
16. Dans la page prêt, cliquez sur **suivant**.  
  
17. Sur le **l’importation de la stratégie/le vocabulaire** , vérifiez que la commande a réussi, puis cliquez sur **suivant**.  
  
18. Cliquez sur **Terminer**.  
  
19. Redémarrez le **Service de mise à jour du moteur de règles**. En cliquant sur **Démarrer**, puis sur **exécuter**, saisie **services.msc**, puis en cliquant sur **OK**. Dans le **Services (Local)** fenêtre, avec le bouton droit **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.
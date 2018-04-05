---
title: 'Étape 2 : Création de schémas Application LOB Contoso pour le prix et la disponibilité de projets à l’aide de l’Éditeur BizTalk | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOB schemas
ms.assetid: 70e26dc9-4299-4d30-8f8b-5cc3469a2025
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 441bb90c8fa0f2edb271af384e2540a741150137
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-creating-the-contoso-lob-application-schemas-for-the-price-and-availability-project-using-biztalk-editor"></a>Étape 2 : Création de schémas Application LOB Contoso pour le prix et le projet de disponibilité à l’aide de l’Éditeur BizTalk
Dans cette étape, vous générez le schéma à utiliser pour interroger le système ERP de Contoso pour le prix et la disponibilité d’un produit particulier. Vous générez ce schéma en utilisant le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® l’adaptateur SQL pour BizTalk Server.  
  
### <a name="to-update-the-sql-stored-procedure-for-schema-generation"></a>Pour mettre à jour l’instruction SQL de procédure stockée pour la génération de schéma  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans Microsoft SQL Server Management Studio, développez **bases de données**, développez **Contoso**, développez **programmabilité**, puis développez **de procédures stockées** .  
  
3.  Avec le bouton droit **dbo. SP_GetInventoryForProductID**, puis cliquez sur **modifier**.  
  
4.  Dans la fenêtre de requête, insérez une virgule, un espace, puis « xmldata », « for xml auto » qui suit immédiatement. La ligne de code doit être la suivante :  
  
    ```  
    for xml auto, xmldata  
    ```  
  
5.  Cliquez sur **Execute** pour enregistrer les modifications apportées à la procédure stockée.  
  
    > [!NOTE]
    >  Microsoft SQL Server Management Studio laissez ouverte pour exécuter la procédure suivante.  
  
### <a name="to-create-the-contoso-price-and-availability-schema"></a>Pour créer le schéma de Contoso Price et la disponibilité  
  
1.  Ouvrez la solution Contoso dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Dans l’Explorateur de solutions, cliquez sur le **ContosoPriceAndAvailability** de projet, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
3.  Dans la boîte de dialogue Ajouter un Iems généré avec **ajouter les métadonnées de l’adaptateur** sélectionné dans le volet gauche, cliquez sur **ajouter les métadonnées de l’adaptateur** dans le volet droit, puis cliquez sur **ajouter**.  
  
4.  Sur le **Assistant Ajout d’adaptateur** page, sélectionnez **SQL** dans la liste des adaptateurs inscrits, puis cliquez sur **suivant**.  
  
5.  Sur le **les informations de base de données** , cliquez sur **définir**.  
  
6.  Dans la boîte de dialogue Propriétés des liaisons de données, dans la zone **Sélectionnez un serveur ou entrez un nom de serveur** , tapez **localhost**. Sélectionnez **Utiliser la sécurité intégrée de Windows NT**. Pour **sélectionner la base de données sur le serveur**, sélectionnez le **Contoso** base de données à partir de la liste de la base de données. Cliquez sur **OK**.  
  
7.  Sur le **les informations de base de données** , cliquez sur **suivant**.  
  
8.  Sur le **informations de schéma** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Espace de noms cible**|Type **http://Contoso.com/Price**.|  
    |**Sélectionnez le type de port**|Sélectionnez **port d’envoi**.|  
    |**Nom de l’élément racine demande de document**|Type **rootPriceRequest**.|  
    |**Nom d’élément de réponse document racine**|Type **rootPriceResponse**.|  
  
9. Cliquez sur **Suivant**.  
  
10. Sur le **informations de type d’instruction** page, sélectionnez **la procédure stockée**, puis cliquez sur **suivant**.  
  
11. Sur le **instruction informations** page, pour  **\<sélectionner une procédure stockée\>**, sélectionnez **SP_GetInventoryForProductID** à partir de la liste déroulante. Cliquez sur **générer**, puis cliquez sur **suivant**.  
  
12. Sur le **fin de l’Assistant génération de schéma de Transport SQL** , cliquez sur **Terminer** pour importer le schéma dans le projet ContosoPriceAndAvailability BizTalk.  
  
13. Dans l’Explorateur de solutions, cliquez sur le schéma généré (SQLService_Price.xsd), cliquez sur **renommer**et le type **ContosoPriceAndAvailability.xsd** comme nouveau nom pour le schéma. Cliquez sur **Entrée**.  
  
14. Dans la fenêtre Propriétés pour le schéma ContosoPriceAndAvailability, définissez le **nom de Type** propriété **ContosoPriceSchema**.  
  
15. Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] crée une orchestration BizTalk nommée **Biztalkorchestration.odx**. Avec le bouton droit de cette orchestration, puis cliquez sur **supprimer** , car vous n’avez pas besoin de cette orchestration. Dans la fenêtre contextuelle indiquant que l’orchestration est définitivement supprimée, cliquez sur **OK**.  
  
16. Dans Microsoft SQL Server Management Studio, supprimez le `xmldata` prédicat et la virgule à partir de la `SP_GetInventoryForProductID` procédure stockée que vous avez ajouté à l’étape précédente, puis cliquez sur **Execute**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Création de mappages d’application LOB Contoso pour le projet de prix et de disponibilité à l’aide du Mappeur BizTalk](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)
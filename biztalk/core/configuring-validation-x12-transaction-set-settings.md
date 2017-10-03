---
title: "Configuration de la Validation (paramètres X12-Transaction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0245be7f-d212-43b1-bfef-cbcbd851b5c0
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880a8d1e31cbb10f570dcf5e7422a1e61b5cc8d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-x12-transaction-set-settings"></a>Configuration de la validation (X12-Paramètres de documents informatisés)
Les paramètres de validation des documents informatisés définissent les modalités de validation des documents informatisés reçus d'un tiers par BizTalk Server. Ils permettent notamment de spécifier le type de validation effectué par BizTalk Server sur les échanges entrants.  
  
> [!NOTE]
>  Cette rubrique s'applique également aux paramètres de validation HIPAA.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-validation-settings"></a>Pour configurer les paramètres de validation  
  
1.  Créer un accord sur comme décrit dans le codage de X12 [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **Validation**.  
  
3.  Dans la grille, vous pouvez définir différents paramètres de validation pour différents documents informatisés. Dans le **Validation** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Default**|Activez la case à cocher pour définir un paramètre de validation par défaut.|  
    |**Type de transaction**|Cliquez sur la cellule vide dans la colonne et sélectionnez un type de transaction dans la liste déroulante.|  
    |**Validation de Type EDI**|Sélectionnez cette option pour activer la validation EDI (élément de données) sur le récepteur d'échanges. Ce type de validation inclut la validation EDI des éléments de données de document informatisé, et valide les types de données, les restrictions de longueur, les éléments de données vides et les séparateurs de fin. Pour plus d’informations, consultez [la Validation de Type EDI (élément de données)](../core/edi-type-data-element-validation.md). **Remarque :** même si cette propriété n’est pas sélectionnée, validation de champ croisé/segment sera exécutée si elle est activée dans l’annotation de schéma.|  
    |**Validation étendue**|Sélectionnez cette option pour activer la validation étendue (BizTalk XSD) des échanges reçus de l'expéditeur. Ceci inclut la validation de la longueur de champ, du caractère facultatif et du nombre de répétitions, outre la validation du type de données XSD. Pour plus d’informations, consultez [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md). **Remarque :** vous pouvez sélectionner cette case à cocher uniquement si **Validation de Type Edi** est sélectionnée.|  
    |**Autoriser les zéros et les espaces de début et de fin**|Sélectionnez cette option pour indiquer que la validation d'un échange EDI reçu d'un tiers n'échouera pas si un élément de données n'est pas conforme aux exigences de longueur en raison de zéros de début (ou de fin) et d'espaces de fin, mais l'est si ceux-ci sont supprimés. **Remarque :** vous pouvez sélectionner cette case à cocher uniquement si **Validation de Type Edi** est sélectionnée.|  
    |**Stratégie de séparateur de fin**|-Sélectionnez **interdit** si vous ne souhaitez pas autoriser les délimiteurs et séparateurs dans un échange reçu de l’expéditeur. Si un échange contient des délimiteurs et des séparateurs de fin, il est déclaré non valide.<br />-Sélectionnez **facultatif** pour accepter les échanges avec ou sans délimiteurs et séparateurs.<br />-Sélectionnez **obligatoire** si l’échange reçu doit contenir des délimiteurs et séparateurs.|  
  
     Vous pouvez ajouter autant de lignes que vous le souhaitez pour définir les paramètres de validation d'échanges spécifiques.  
  
     Pour supprimer un paramètre de validation, sélectionnez la ligne, puis cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  La modification des propriétés dans la grille peut présenter quelques difficultés. Au lieu de cela, vous pouvez sélectionner la ligne à modifier, puis modifiez les mêmes propriétés dans le **modifier les lignes sélectionnées** section. Les paramètres indiqués ici sont répercutés dans la ligne sélectionnée.  
  
4.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des paramètres (X12) documents informatisés](../core/configuring-transaction-set-settings-x12.md)
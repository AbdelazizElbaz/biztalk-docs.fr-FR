---
title: "Configuration de la Validation (EDIFACT-informatisés paramètres) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b30a78-3a4b-4827-9b0a-af9ad3e865a3
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a9ad8f69accd0f479e05e130cc0c28fe874bb86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-validation-edifact-transaction-set-settings"></a>Configuration de la validation (EDIFACT - Paramètres de documents informatisés)
Les paramètres de validation des documents informatisés définissent les modalités de validation des documents informatisés reçus d'un tiers par BizTalk Server. Ils permettent notamment de spécifier le type de validation effectué par BizTalk Server sur les échanges entrants.  
  
> [!IMPORTANT]
>  Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-ack-processing-and-validation-settings"></a>Pour configurer le traitement des accusés de réception et les paramètres de validation  
  
1.  Créer un accord le codage comme décrit dans EDIFACT, [paramètres généraux configuration (EDIFACT)](../core/configuring-general-settings-edifact.md). Pour mettre à jour un accord existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.  
  
2.  Sous l’onglet accord unidirectionnel, sous **paramètres des documents informatisés** , cliquez sur **Validation**.  
  
3.  Dans la grille, vous pouvez définir différents paramètres de validation pour différents documents informatisés. Dans le **Validation** page, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Default**|Activez la case à cocher pour définir un paramètre de validation par défaut.|  
    |**UNH2.1**|Cliquez sur la cellule vide dans la colonne et sélectionnez un type de transaction dans la liste déroulante.|  
    |**Validation de Type EDI**|Sélectionnez **type EDI** pour activer la validation EDI (élément de données) sur le récepteur d’échanges. Ce type de validation inclut la validation EDI des éléments de données de document informatisé, et valide les types de données, les restrictions de longueur, les éléments de données vides et les séparateurs de fin. Pour plus d’informations, consultez [la Validation de Type EDI (élément de données)](../core/edi-type-data-element-validation.md). **Remarque :** même si cette propriété n’est pas sélectionnée, validation de champ croisé/segment sera exécutée si elle est activée dans l’annotation de schéma.|  
    |**Validation étendue**|Sélectionnez cette option pour activer la validation étendue (BizTalk XSD) des échanges reçus de l'expéditeur. Ceci inclut la validation de la longueur de champ, du caractère facultatif et du nombre de répétitions, outre la validation du type de données XSD. Pour plus d’informations, consultez [Validation étendue (BTS-XSD)](../core/extended-bts-xsd-validation.md). **Remarque :** vous pouvez sélectionner cette case à cocher uniquement si **Validation de Type Edi** est sélectionnée.|  
    |**Autoriser les zéros et les espaces de début et de fin**|Sélectionnez cette option pour indiquer que la validation d'un échange EDI reçu d'un tiers n'échouera pas si un élément de données n'est pas conforme aux exigences de longueur en raison de zéros de début (ou de fin) et d'espaces de fin, mais l'est si ceux-ci sont supprimés. **Remarque :** vous pouvez sélectionner cette case à cocher uniquement si **Validation de Type Edi** est sélectionnée.|  
    |**Stratégie de séparateur de fin**|-Sélectionnez **interdit** si vous ne souhaitez pas autoriser les délimiteurs et séparateurs dans un échange reçu de l’expéditeur. Si un échange contient des délimiteurs et des séparateurs de fin, il est déclaré non valide.<br />-Sélectionnez **facultatif** pour accepter les échanges avec ou sans délimiteurs et séparateurs.<br />-Sélectionnez **obligatoire** si l’échange reçu doit contenir des délimiteurs et séparateurs.|  
  
     Vous pouvez ajouter autant de lignes que vous le souhaitez pour définir les paramètres de validation d'échanges spécifiques.  
  
     Pour supprimer un paramètre de validation, sélectionnez la ligne, puis cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  La modification des propriétés dans la grille peut présenter quelques difficultés. Au lieu de cela, vous pouvez sélectionner la ligne à modifier, puis modifiez les mêmes propriétés dans le **modifier les lignes sélectionnées** section. Les paramètres indiqués ici sont répercutés dans la ligne sélectionnée.  
  
4.  Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des documents informatisés (EDIFACT) de paramètres](../core/configuring-transaction-set-settings-edifact.md)
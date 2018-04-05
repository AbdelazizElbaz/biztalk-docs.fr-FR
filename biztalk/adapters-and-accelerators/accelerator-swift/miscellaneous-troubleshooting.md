---
title: Résolution des problèmes divers | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting
ms.assetid: 6ebc1867-b5d3-46de-b3bd-69e570ed2b2c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 765b32895fa76c0c77b740b76e2e6a03f0571351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="miscellaneous-troubleshooting"></a>Résolution des problèmes divers
## <a name="leading-zeroes-validation-is-not-performed-for-fields-that-use-the-checkleadingzeroesinelement-method-to-validate-a-field-in-the-message-validation-policy"></a>Les zéros de début validation n’est pas effectuée pour les champs qui utilisent la méthode CheckLeadingZeroesInElement pour valider un champ dans la stratégie de Validation de message.  
  
### <a name="symptom"></a>Symptôme  
 Aucune erreur de validation BRE n’est retournée si un message est envoyé avec des zéros non significatifs dans un champ, même si les zéros non significatifs ne sont pas autorisées pour le champ et de la stratégie de validation comprend une règle pour le champ qui effectue cette validation.  
  
### <a name="possible-cause"></a>Cause possible  
 Le **CheckLeadingZeroInElement** (méthode) est incluse dans une règle d’entreprise dans la stratégie de validation pour le type de message. Cette méthode est déconseillée. L’objectif de l’appel de fonction doit entraîner une validation échoue s’il existe un zéro non significatif dans l’élément fourni dans l’appel de fonction. Toutefois, cette méthode ne provoque pas de validation échoue, même s’il existe un zéro non significatif dans le champ.  
  
### <a name="solution"></a>Solution  
 Si vous souhaitez vérifier les zéros non significatifs, vous devez implémenter la **CheckLeadingZero** méthode au lieu du **CheckLeadingZeroInElement** (méthode). **CheckLeadingZero** provoque une erreur de validation s’il existe un zéro non significatif de l’entrée de chaîne à la fonction.  
  
 Pour implémenter le **CheckLeadingZero** (méthode), vous devez créer une méthode personnalisée qui appelle le **CheckLeadingZero** méthode à partir de la fonction personnalisée et fournit à celui-ci sous forme de chaîne, la valeur est validé pour les zéros de début. C’est parce que **CheckLeadingZero** n’enregistre pas d’une erreur, mais simplement retourne une valeur booléenne False si la chaîne d’entrée n’est pas un champ de numéro de SWIFT valide ou si l’entrée de chaîne contient un zéro non significatif. Sinon, elle retourne la valeur True. Votre méthode personnalisée peut ensuite enregistrent des erreurs en conséquence.  
  
## <a name="an-error-is-returned-by-the-message-validation-policy-if-the-swift-number-field-has-a-leading-zero"></a>Une erreur est retournée par la stratégie de validation de message si le champ de numéro de SWIFT a un zéro non significatif  
  
### <a name="symptom"></a>Symptôme  
 Une erreur de validation BRE est retournée si un message est envoyé avec des zéros non significatifs dans un champ de même si le début des zéros sont autorisées pour le champ.  
  
### <a name="possible-cause"></a>Cause possible  
 Cela peut se produire si une des méthodes suivantes est utilisée pour valider un champ de numéro de SWIFT dans la règle concernée, généralement à la partie de l’Action de la règle. Cela peut se produire dans un champ Quantité, taux, prix ou la quantité.  
  
-   **CheckCurrencyAmount**  
  
-   **CheckValidAmount**  
  
-   **CheckValidCurrencyAndPriceCode**  
  
-   **CheckValidSignCurrencyAmount**  
  
-   **CheckValidSignDateCurrencyAmount**  
  
-   **CheckValidSignRate**  
  
-   **IsValidTransactionDetailsCurrencyAmount**  
  
### <a name="solution"></a>Solution  
 Si une des méthodes dans la liste ci-dessus, à l’exception de **CheckValidSignRate**, est utilisé dans la règle de la stratégie de Validation, activer des zéros non significatifs, comme décrit dans [prise en charge des zéros non significatifs dans les Validations de champ Quantité](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).  
  
 Si le **CheckValidSignRate** méthode est utilisée dans la règle qui a retourné l’erreur, la seule façon pour prendre en charge les zéros non significatifs consiste à supprimer cette règle de la stratégie de Validation. Suivez les étapes ci-dessous pour effectuer cette opération :  
  
1.  Dans l’éditeur des règles d’entreprise, cliquez sur le **Version** nœud pour la stratégie déployée qui contient une règle à l’aide de la **CheckValidSignRate** (méthode). Cliquez sur **Annuler le déploiement**.  
  
2.  Cliquez sur le **Version** nœud pour la même stratégie, puis cliquez sur **copie**.  
  
3.  Cliquez sur le **Validation_Policy** nœud pour la même stratégie, puis cliquez sur **coller**.  
  
4.  Développez la nouvelle version non enregistrée de la stratégie. Avec le bouton droit de la règle qui a le **CheckValidSignRate** appel de méthode, puis cliquez sur **supprimer**.  
  
5.  Avec le bouton de la stratégie de non enregistrées new **Version** nœud, puis cliquez sur **enregistrer**. Cliquez sur le même nœud, puis cliquez sur **publier**. Cliquez sur le même nœud, puis cliquez sur **déployer**.  
  
## <a name="a4swift-database-requires-archiving"></a>Base de données A4SWIFT requiert l’archivage  
  
### <a name="symptom"></a>Symptôme  
 Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données est trop importante.  
  
### <a name="possible-cause"></a>Cause possible  
 La table d’historique dans les [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données n’est pas automatiquement archivé. Cette table stocke des données sur le message repair et nouvelle soumission, y compris les personnes qui ont effectué les tâches et les données sur les processus d’orchestration. Cette table continue à croître à mesure que vous effectuez des opérations d’envoi et de la réparation de message.  
  
### <a name="solution"></a>Solution  
 Pour limiter la croissance de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] de base de données, d’archiver régulièrement les données en dehors de la table d’historique, à l’aide de vos procédures d’archivage de standard.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes : Problèmes et résolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)
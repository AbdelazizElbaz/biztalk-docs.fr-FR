---
title: "Utilisation de la Validation de la règle de suppression | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, deleting rules
- rules
ms.assetid: b2b0dabf-8f99-4b85-95da-6bbf3e79ad41
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59aea2c772f1906ca779187f22a094e3f6cb4ceb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="removing-usage-rule-validation"></a><span data-ttu-id="ef166-102">Utilisation de la Validation de la règle de suppression</span><span class="sxs-lookup"><span data-stu-id="ef166-102">Removing Usage Rule Validation</span></span>
<span data-ttu-id="ef166-103">Règles d’utilisation sont définies dans les normes SWIFT et appliquées par [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] les stratégies d’entreprise spécifiques à chaque type de message.</span><span class="sxs-lookup"><span data-stu-id="ef166-103">Usage rules are defined in SWIFT standards and enforced by [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business policies specific to each message type.</span></span> <span data-ttu-id="ef166-104">Ces règles d’utilisation des instructions que vous pouvez utiliser pour fournir la validation supplémentaire pour un champ.</span><span class="sxs-lookup"><span data-stu-id="ef166-104">These usage rules are guidelines that you can use to provide extra validation for a field.</span></span> <span data-ttu-id="ef166-105">Contrairement aux règles de validation de réseau, qui sont obligatoires, vous pouvez choisir ne pas pour les règles d’utilisation pour un type de message.</span><span class="sxs-lookup"><span data-stu-id="ef166-105">Unlike network validation rules, which are mandatory, you can choose not to require usage rules for a message type.</span></span> <span data-ttu-id="ef166-106">Si tel est le cas, vous pouvez effectuer l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef166-106">If that is the case, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="ef166-107">Vous pouvez supprimer une règle d’entreprise spécifique qui applique une règle d’utilisation de la stratégie de validation de type de message.</span><span class="sxs-lookup"><span data-stu-id="ef166-107">You can remove a specific business rule that enforces a usage rule from the message-type validation policy.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ef166-108">Suppression d’une règle de la stratégie supprime définitivement.</span><span class="sxs-lookup"><span data-stu-id="ef166-108">Removing a rule from the policy will remove it permanently.</span></span>  
  
-   <span data-ttu-id="ef166-109">Si vous ne souhaitez pas appliquer les règles d’utilisation, vous pouvez annuler le déploiement de la stratégie de validation pour un type de message.</span><span class="sxs-lookup"><span data-stu-id="ef166-109">If you do not want to enforce any of the usage rules, you can undeploy the validation policy for a message type.</span></span>  
  
### <a name="to-remove-a-rule-from-a-policy"></a><span data-ttu-id="ef166-110">Pour supprimer une règle d’une stratégie</span><span class="sxs-lookup"><span data-stu-id="ef166-110">To remove a rule from a policy</span></span>  
  
1.  <span data-ttu-id="ef166-111">Dans un éditeur de texte, tel que le bloc-notes, ouvrez la stratégie de validation que vous souhaitez modifier, par exemple, MT103_Validation_Policy dans  *\<lecteur >*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \< version > Message Pack\SWIFT Messages\A4SWIFT-SRG\<version > \Category 1\MT103.</span><span class="sxs-lookup"><span data-stu-id="ef166-111">In a text editor, such as Notepad, open the validation policy that you want to change, for example, MT103_Validation_Policy in *\<drive>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version>\Category 1\MT103.</span></span>  
  
2.  <span data-ttu-id="ef166-112">Supprimez le nœud de règle que vous ne pas souhaitez, puis enregistrez la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ef166-112">Remove the rule node that you do not want, and then save the policy.</span></span>  
  
3.  <span data-ttu-id="ef166-113">Utilisez l’Assistant de déploiement de moteur de règles d’entreprise à publier et déployer la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ef166-113">Use the Business Rules Engine Deployment Wizard to publish and deploy the policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef166-114">Vous pouvez également supprimer une règle à partir d’une stratégie de validation en créant une copie de la stratégie, suppression de la règle spécifique et puis de déployer la stratégie modifiée.</span><span class="sxs-lookup"><span data-stu-id="ef166-114">You can also remove a rule from a validation policy by creating a copy of the policy, removing the specific rule, and then deploying the modified policy.</span></span> <span data-ttu-id="ef166-115">Annuler le déploiement de la version précédente de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="ef166-115">Undeploy the previous version of the policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef166-116">Dans l’éditeur des règles d’entreprise, vous ne pouvez pas supprimer une règle à partir d’une stratégie de publié ou déployée.</span><span class="sxs-lookup"><span data-stu-id="ef166-116">In Business Rule Composer, you cannot delete a rule from a published or deployed policy.</span></span>  
  
### <a name="to-remove-the-policy-for-a-message-type"></a><span data-ttu-id="ef166-117">Pour supprimer la stratégie pour un type de message</span><span class="sxs-lookup"><span data-stu-id="ef166-117">To remove the policy for a message type</span></span>  
  
1.  <span data-ttu-id="ef166-118">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="ef166-118">Click **Start**, point to **Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="ef166-119">Dans l’Explorateur de stratégies, de trouver la stratégie de validation déployé pour le type de message, par exemple, MT103_Validation_Policy.</span><span class="sxs-lookup"><span data-stu-id="ef166-119">In Policy Explorer, find the deployed validation policy for the message type, for example, MT103_Validation_Policy.</span></span>  
  
3.  <span data-ttu-id="ef166-120">Avec le bouton droit de la stratégie, cliquez sur **annuler le déploiement**, cliquez sur **supprimer**, puis cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="ef166-120">Right-click the policy, click **Undeploy**, click **Delete**, and then click **Yes**.</span></span>
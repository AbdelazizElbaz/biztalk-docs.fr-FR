---
title: "Comment attribuer des Values1 de propriété de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e76c62-3110-482c-8083-84d411e6f475
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39bb2a4c6520c1ff3a21889e7508bb2cf417b817
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-message-context-property-values"></a><span data-ttu-id="d2f09-102">Affectation de valeurs aux propriétés de contexte d'un message</span><span class="sxs-lookup"><span data-stu-id="d2f09-102">How to Assign Message Context Property Values</span></span>
<span data-ttu-id="d2f09-103">Pour gérer la session de connexion de l'adaptateur JD Edwards OneWorld à partir d'une orchestration BizTalk, vous devez ajouter la référence à Microsoft.BizTalk.Adapters.JDEProperties.dll dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="d2f09-103">To manage the JD Edwards EnterpriseOne Adapter connection session from a BizTalk orchestration, you must add the reference to Microsoft.BizTalk.Adapters.JDEProperties.dll in your project.</span></span> <span data-ttu-id="d2f09-104">Cet assembly se trouve dans le répertoire %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span><span class="sxs-lookup"><span data-stu-id="d2f09-104">This assembly is located in %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
 <span data-ttu-id="d2f09-105">Une fois ce schéma de propriété référencé, d'autres propriétés de contexte sont accessibles à divers outils de développement BizTalk (par exemple, forme Assignation du message au sein du Concepteur d'orchestration).</span><span class="sxs-lookup"><span data-stu-id="d2f09-105">After you reference this property schema, additional context properties are accessible to various BizTalk development tools, for example, the Message Assignment shape within the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="d2f09-106">Pour accéder à une propriété de contexte, vous devez spécifier une des propriétés de contexte disponibles dans l'espace de noms JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="d2f09-106">To access a context property, you specify one of the available context properties within the JD Edwards EnterpriseOne namespace.</span></span> <span data-ttu-id="d2f09-107">Pour lire la propriété de contexte d'un message reçu d'un port lié à l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, vous devez utiliser la syntaxe Message(JDE.Property) dans une expression.</span><span class="sxs-lookup"><span data-stu-id="d2f09-107">To read a context property of a message received from a port bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the syntax, Message(JDE.Property), in an expression.</span></span> <span data-ttu-id="d2f09-108">Consultez la gestion de session de l'adaptateur JD Edwards EnterpriseOne pour obtenir la liste des propriétés.</span><span class="sxs-lookup"><span data-stu-id="d2f09-108">Refer to JD Edwards EnterpriseOne Adapter Session Management for a list of properties.</span></span>  
  
 <span data-ttu-id="d2f09-109">Dans BizTalk, les messages sont immuables.</span><span class="sxs-lookup"><span data-stu-id="d2f09-109">In BizTalk, messages are immutable.</span></span>  
  
### <a name="to-assign-context-property-value"></a><span data-ttu-id="d2f09-110">Pour affecter une valeur de propriété de contexte</span><span class="sxs-lookup"><span data-stu-id="d2f09-110">To assign context property value</span></span>  
  
1.  <span data-ttu-id="d2f09-111">Créez un message.</span><span class="sxs-lookup"><span data-stu-id="d2f09-111">Create a new message.</span></span>  
  
2.  <span data-ttu-id="d2f09-112">Définissez-en le contenu (par exemple, en assignant un message existant).</span><span class="sxs-lookup"><span data-stu-id="d2f09-112">Set the message content, for example, by assigning an existing message.</span></span>  
  
3.  <span data-ttu-id="d2f09-113">Définissez les propriétés.</span><span class="sxs-lookup"><span data-stu-id="d2f09-113">Set the properties.</span></span>  
  
 <span data-ttu-id="d2f09-114">Pour affecter les propriétés de contexte à un message destiné à un port d'envoi lié à l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, utilisez l'opérateur d'assignation de message.</span><span class="sxs-lookup"><span data-stu-id="d2f09-114">To assign context properties to a message destined to a send port that is bound to the Microsoft BizTalk Adapter for JD Edwards EnterpriseOne, use the message assignment operator.</span></span> <span data-ttu-id="d2f09-115">Spécifiez ensuite une des propriétés de contexte disponibles dans l'espace de noms JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="d2f09-115">Then specify one of the available context properties within the JD Edwards EnterpriseOne namespace.</span></span>  
  
 <span data-ttu-id="d2f09-116">La syntaxe est la suivante :`Message(JDE.Property) = value;`</span><span class="sxs-lookup"><span data-stu-id="d2f09-116">The syntax is: `Message(JDE.Property) = value;`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f09-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2f09-117">See Also</span></span>  
 <span data-ttu-id="d2f09-118">[À l’aide des propriétés de contexte de Message](../core/using-message-context-properties1.md) </span><span class="sxs-lookup"><span data-stu-id="d2f09-118">[Using Message Context Properties](../core/using-message-context-properties1.md) </span></span>  
 <span data-ttu-id="d2f09-119">[Sur la gestion de Session](../core/about-session-management2.md) </span><span class="sxs-lookup"><span data-stu-id="d2f09-119">[About Session Management](../core/about-session-management2.md) </span></span>  
 [<span data-ttu-id="d2f09-120">Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="d2f09-120">Tutorial: Using the BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone.md)
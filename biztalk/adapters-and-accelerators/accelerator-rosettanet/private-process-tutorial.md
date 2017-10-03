---
title: "Didacticiel sur les processus privés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, tutorial
- private process tutorial
- tutorials, private process tutorial
ms.assetid: 58affc48-af73-406e-895f-696bc284d945
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c017d8b9b52c1f477aba62308ca2e65a1550564
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="private-process-tutorial"></a><span data-ttu-id="ba778-102">Didacticiel sur les processus privés</span><span class="sxs-lookup"><span data-stu-id="ba778-102">Private Process Tutorial</span></span>
<span data-ttu-id="ba778-103">Ce didacticiel contient une solution complète de bout en bout à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ba778-103">This tutorial contains a complete end-to-end solution using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="ba778-104">Le didacticiel détaille les étapes à suivre pour implémenter une solution compatible avec RosettaNet en créant un scénario commercial entre deux entreprises fictives : Contoso, l’organisation du fournisseur et Fabrikam, l’organisation de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="ba778-104">The tutorial details the steps that you have to follow to implement a RosettaNet-compliant solution by creating a trading scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>  
  
 <span data-ttu-id="ba778-105">Le scénario qu'implémente de ce didacticiel utilise le 3A2-prix et la disponibilité des processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="ba778-105">The scenario this tutorial implements uses the 3A2-Price and Availability Partner Interface Process (PIP).</span></span> <span data-ttu-id="ba778-106">Avant un achat, l’acheteur, Fabrikam, envoie un prix 3A2 et disponibilité demander au fournisseur, Contoso.</span><span class="sxs-lookup"><span data-stu-id="ba778-106">Before a purchase, the buyer, Fabrikam, sends a 3A2-Price and Availability Request to the supplier, Contoso.</span></span> <span data-ttu-id="ba778-107">Ce processus PIP permet de Fabrikam obtenir des informations de produits qu’ils peuvent alors traiter par le biais des règles d’entreprise pour déterminer s’il faut acheter le produit.</span><span class="sxs-lookup"><span data-stu-id="ba778-107">This PIP enables Fabrikam to obtain information about a certain product that they can then process through business rules to make a determination about whether to purchase the product.</span></span> <span data-ttu-id="ba778-108">La figure suivante illustre le modèle de communication entre les organisations initiateur et le répondeur lors d’un échange PIP 3A2.</span><span class="sxs-lookup"><span data-stu-id="ba778-108">The following figure shows the communication pattern between the initiator and responder organizations during a 3A2 PIP exchange.</span></span>  
  
 <span data-ttu-id="ba778-109">![&#60; Aucune modification &#62; ] (../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a2flow.gif "RN3_Intro_EETut_3A2Flow")</span><span class="sxs-lookup"><span data-stu-id="ba778-109">![&#60;No Change&#62;](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-intro-eetut-3a2flow.gif "RN3_Intro_EETut_3A2Flow")</span></span>  
  
 <span data-ttu-id="ba778-110">L’objectif de ce didacticiel est la solution Contoso.</span><span class="sxs-lookup"><span data-stu-id="ba778-110">The focus of this tutorial is on the Contoso solution.</span></span> <span data-ttu-id="ba778-111">Il décrit divers aspects de la création d’une solution RosettaNet, notamment l’intégration ERP, application de la stratégie, personnalisation de processus privé et promouvoir une communication sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ba778-111">It outlines various aspects of creating a RosettaNet-based solution, including ERP integration, business policy enforcement, private process customization, and promoting secure communication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba778-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ba778-112">In This Section</span></span>  
  
-   [<span data-ttu-id="ba778-113">Préparation pour le didacticiel sur les processus privés</span><span class="sxs-lookup"><span data-stu-id="ba778-113">Preparing for the Private Process Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-private-process-tutorial.md)  
  
-   [<span data-ttu-id="ba778-114">Création de la Solution de Contoso</span><span class="sxs-lookup"><span data-stu-id="ba778-114">Creating the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-solution.md)  
  
-   [<span data-ttu-id="ba778-115">Création de la Solution Fabrikam</span><span class="sxs-lookup"><span data-stu-id="ba778-115">Creating the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)  
  
-   [<span data-ttu-id="ba778-116">Test de la Solution</span><span class="sxs-lookup"><span data-stu-id="ba778-116">Testing the Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-solution.md)
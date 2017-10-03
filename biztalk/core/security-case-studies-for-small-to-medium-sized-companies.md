---
title: "Études de cas de sécurité pour les petites et moyennes entreprises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
- security, examples
- security, architecture
- architecture, medium distributions
ms.assetid: b33e3f2a-ddc4-47a8-92d7-511ae0cc880e
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9af0f013960e882ffe6b5c081ae1452df4aaecf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-case-studies-for-small-to-medium-sized-companies"></a><span data-ttu-id="12404-102">Études de cas de sécurité pour les petites et moyennes entreprises</span><span class="sxs-lookup"><span data-stu-id="12404-102">Security Case Studies for Small to Medium-Sized Companies</span></span>
<span data-ttu-id="12404-103">La sécurité se situe au centre des préoccupations de toute entreprise soucieuse de garantir que ses données et ressources ne pourront être accédées que par un groupe de personnes ou d'applications bien déterminé.</span><span class="sxs-lookup"><span data-stu-id="12404-103">Security is a concern of any company that is serious about making sure that only a select group of people or applications can access its data and resources.</span></span> <span data-ttu-id="12404-104">Les entreprises considèrent et implémentent la sécurité de plusieurs manières.</span><span class="sxs-lookup"><span data-stu-id="12404-104">Companies approach and implement security in a variety of ways.</span></span>  
  
 <span data-ttu-id="12404-105">Cette section fournit des instructions permettant de déployer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au sein d'un environnement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="12404-105">This section provides guidelines for deploying Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a secure environment.</span></span> <span data-ttu-id="12404-106">Elle dispense également des informations vous permettant d'évaluer les menaces potentielles planant sur votre implémentation de BizTalk Server ainsi qu'un exemple d'architecture pour les petites et moyennes entreprises.</span><span class="sxs-lookup"><span data-stu-id="12404-106">It provides information to help you assess the potential threats to your BizTalk Server implementation, a sample architecture for small and medium-size companies.</span></span>  
  
 <span data-ttu-id="12404-107">De nos jours, il est difficile de diriger une entreprise sans prendre en considération l'aspect de sécurité.</span><span class="sxs-lookup"><span data-stu-id="12404-107">It is difficult to run a business today without thinking about security.</span></span> <span data-ttu-id="12404-108">Si vous effectuez des transactions en ligne, vous souhaiterez sans doute protéger les informations concernant les cartes de crédit de vos clients.</span><span class="sxs-lookup"><span data-stu-id="12404-108">If you carry out online transactions, you want to protect the credit card information of your customers.</span></span> <span data-ttu-id="12404-109">Si vous travaillez pour le compte d'une grande entreprise, vous chercherez certainement à tenir les utilisateurs malveillants à l'écart de vos réseaux.</span><span class="sxs-lookup"><span data-stu-id="12404-109">If you work for a Fortune 500 company, you want to keep malicious users away from your networks.</span></span> <span data-ttu-id="12404-110">Si vous êtes un utilisateur d'ordinateur, vous souhaiterez empêcher qu'un virus ou un vers n'endommage vos données et limite de ce fait votre capacité à mener à bien votre travail.</span><span class="sxs-lookup"><span data-stu-id="12404-110">If you are a desktop user, you want to keep viruses and worms from damaging your data and limiting your ability to do your work.</span></span> <span data-ttu-id="12404-111">Vous entendez presque tous les jours parler de nouvelles vulnérabilités logicielles, de nouveaux vers ou virus qui se propagent toujours plus rapidement tout en étant toujours plus difficiles à neutraliser ou encore de sites Web d'entreprises dévastés par des utilisateurs malveillants.</span><span class="sxs-lookup"><span data-stu-id="12404-111">Almost every day you hear or read about new software vulnerabilities; about new worms and viruses that are faster spreading, harder to eradicate, and more damaging than the previous ones; and about the Web sites of companies being defaced by malicious users.</span></span> <span data-ttu-id="12404-112">Quelle que soit la taille de votre entreprise, quel que soit le nombre de vos clients, quel que soit la taille de votre parc informatique, vous devez empêcher les utilisateurs malveillants et les programmes (virus ou vers) de compromettre l'intégrité de vos données, de vos ordinateurs ou de la capacité à mener à bien votre activité.</span><span class="sxs-lookup"><span data-stu-id="12404-112">Whatever your business is—large or small, a few customers or millions of customers, one computer or hundreds of computers—you need to keep malicious users and programs (viruses, worms) from compromising your data, computers, and ability to do your job.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12404-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="12404-113">In This Section</span></span>  
  
-   [<span data-ttu-id="12404-114">Études de cas de sécurité : La société A</span><span class="sxs-lookup"><span data-stu-id="12404-114">Security Case Studies: Company A</span></span>](../core/security-case-studies-company-a.md)  
  
-   [<span data-ttu-id="12404-115">Études de cas de sécurité : La société B</span><span class="sxs-lookup"><span data-stu-id="12404-115">Security Case Studies: Company B</span></span>](../core/security-case-studies-company-b.md)  
  
-   [<span data-ttu-id="12404-116">Analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="12404-116">Threat Model Analysis</span></span>](../core/threat-model-analysis.md)  
  
-   [<span data-ttu-id="12404-117">Exemples d’architecture pour les petites et moyennes entreprises</span><span class="sxs-lookup"><span data-stu-id="12404-117">Sample Architectures for Small & Medium-Sized Companies</span></span>](../core/sample-architectures-for-small-medium-sized-companies.md)  
  
-   [<span data-ttu-id="12404-118">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="12404-118">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)
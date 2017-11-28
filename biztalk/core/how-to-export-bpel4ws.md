---
title: Comment exporter BPEL4WS | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPEL4WS, exporting
- BPEL4WS, restrictions
- orchestrations, BPEL4WS
ms.assetid: 4648dfcf-cf48-4471-b088-07252c080fb8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16c2e34b498a9fb8d5fd3f6e69f022c2876a763
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-export-bpel4ws"></a><span data-ttu-id="fda2b-102">Comment exporter BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="fda2b-102">How to Export BPEL4WS</span></span>
<span data-ttu-id="fda2b-103">Vous pouvez exporter une orchestration BizTalk existante vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="fda2b-103">You can export an existing BizTalk orchestration to BPEL4WS.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fda2b-104">Cette version de BizTalk Server est compatible avec BPEL4WS 1.1.</span><span class="sxs-lookup"><span data-stu-id="fda2b-104">This release of BizTalk Server supports BPEL4WS 1.1.</span></span> <span data-ttu-id="fda2b-105">Vous ne pouvez pas importer ni exporter BPEL4WS 1.0.</span><span class="sxs-lookup"><span data-stu-id="fda2b-105">You cannot import or export BPEL4WS 1.0.</span></span>  
  
 <span data-ttu-id="fda2b-106">Si vous effectuez une exportation, la compatibilité de BPEL4WS pour la compilation exige que les orchestrations ne contiennent que des composants communs à XLANG/s et à BPEL4WS, ou des composants pouvant être convertis en BPEL4WS sans que leur comportement n'en soit modifié.</span><span class="sxs-lookup"><span data-stu-id="fda2b-106">If you are exporting, BPEL4WS compliance for compilation requires that orchestrations contain only features that are common between XLANG/s and BPEL4WS, or features that can be translated into BPEL4WS without affecting behavior.</span></span>  
  
## <a name="export-restrictions-on-orchestrations-for-bpel4ws-compliance"></a><span data-ttu-id="fda2b-107">Limites d’exportation imposées aux orchestrations pour des raisons de compatibilité avec BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="fda2b-107">Export restrictions on orchestrations for BPEL4WS compliance</span></span>  
  
-   <span data-ttu-id="fda2b-108">Vous ne pouvez pas utiliser la forme Appeler orchestration ou la forme Démarrer orchestration.</span><span class="sxs-lookup"><span data-stu-id="fda2b-108">You cannot use the Call Orchestration shape or the Start Orchestration shape.</span></span>  
  
-   <span data-ttu-id="fda2b-109">Vous ne pouvez pas utiliser la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="fda2b-109">You cannot use the Transform shape.</span></span>  
  
-   <span data-ttu-id="fda2b-110">Vous ne pouvez pas appeler de méthodes sur les composants .NET personnalisés.</span><span class="sxs-lookup"><span data-stu-id="fda2b-110">You cannot invoke methods on custom .NET components.</span></span>  
  
-   <span data-ttu-id="fda2b-111">Vous ne pouvez pas appliquer un délai à une transaction à long terme.</span><span class="sxs-lookup"><span data-stu-id="fda2b-111">You cannot apply a timeout to a long-running transaction.</span></span>  
  
-   <span data-ttu-id="fda2b-112">Votre orchestration ne peut pas accepter de paramètres.</span><span class="sxs-lookup"><span data-stu-id="fda2b-112">Your orchestration cannot take parameters.</span></span>  
  
-   <span data-ttu-id="fda2b-113">Les gestionnaires de compensation pouvant être appelés ne peuvent pas avoir de paramètres.</span><span class="sxs-lookup"><span data-stu-id="fda2b-113">Callable compensation handlers cannot have parameters.</span></span>  
  
-   <span data-ttu-id="fda2b-114">Les types de variables doivent être pris en charge dans XPATH.</span><span class="sxs-lookup"><span data-stu-id="fda2b-114">Variable types must be supportable in XPATH.</span></span>  
  
-   <span data-ttu-id="fda2b-115">Vous ne pouvez pas utiliser la forme Interrompre.</span><span class="sxs-lookup"><span data-stu-id="fda2b-115">You cannot use the Suspend shape.</span></span>  
  
-   <span data-ttu-id="fda2b-116">Les valeurs littérales doivent être un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="fda2b-116">Literal values must be one of the following types:</span></span>  
  
     <span data-ttu-id="fda2b-117">boolean, char, byte, sbyte, int32, uint32, int64, uint64, single, double, string</span><span class="sxs-lookup"><span data-stu-id="fda2b-117">boolean, char, byte, sbyte, int32, uint32, int64, uint64, single, double, string</span></span>  
  
-   <span data-ttu-id="fda2b-118">Les opérateurs arithmétiques ne sont autorisés que sur les opérandes de types numériques suivants :</span><span class="sxs-lookup"><span data-stu-id="fda2b-118">Arithmetic operators are allowed only on operands of following numeric types:</span></span>  
  
     <span data-ttu-id="fda2b-119">byte, sbyte, int32, uint32, int64, uint64, single, double</span><span class="sxs-lookup"><span data-stu-id="fda2b-119">byte, sbyte, int32, uint32, int64, uint64, single, double</span></span>  
  
-   <span data-ttu-id="fda2b-120">Les opérateurs relationnels ne peuvent pas être appliqués au type char.</span><span class="sxs-lookup"><span data-stu-id="fda2b-120">Relational operators cannot be applied to type char.</span></span>  
  
-   <span data-ttu-id="fda2b-121">Vous ne pouvez pas faire référence à une propriété de liaison de service dans une expression.</span><span class="sxs-lookup"><span data-stu-id="fda2b-121">You cannot make a reference to a servicelink property in an expression.</span></span>  
  
-   <span data-ttu-id="fda2b-122">Vous ne pouvez pas effectuer d’actions entre un **envoyer** forme et un **réception** forme qui utilisent le même port requête-réponse sortant.</span><span class="sxs-lookup"><span data-stu-id="fda2b-122">You cannot perform any actions between a **Send** shape and a **Receive** shape that use the same outbound request-response port.</span></span>  
  
-   <span data-ttu-id="fda2b-123">Vous ne pouvez pas faire référence à un service Web de façon indirecte, comme à travers une référence à un autre projet contenant une référence.</span><span class="sxs-lookup"><span data-stu-id="fda2b-123">You cannot indirectly reference a web service, as through a reference to another project that contains a reference.</span></span> <span data-ttu-id="fda2b-124">Vous devez explicitement référencer le service Web dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="fda2b-124">You must explicitly reference the web service in your project.</span></span>  
  
-   <span data-ttu-id="fda2b-125">Vous ne pouvez pas indiquer de valeur DateTime ou TimeSpan constante dans un délai.</span><span class="sxs-lookup"><span data-stu-id="fda2b-125">You cannot specify a constant DateTime or TimeSpan in a delay.</span></span> <span data-ttu-id="fda2b-126">Utilisez à la place une des classes de conversion dans l'espace de noms System.Xml :</span><span class="sxs-lookup"><span data-stu-id="fda2b-126">Instead, use one of the conversion classes in the System.Xml namespace:</span></span>  
  
     <span data-ttu-id="fda2b-127">Pour une valeur DateTime constante : System.Xml.XmlConvert.ToDateTime, par exemple System.Xml.XmlConvert.ToDateTime("2004-04-15")</span><span class="sxs-lookup"><span data-stu-id="fda2b-127">For a constant DateTime: System.Xml.XmlConvert.ToDateTime, e.g System.Xml.XmlConvert.ToDateTime("2004-04-15")</span></span>  
  
     <span data-ttu-id="fda2b-128">Pour une valeur TimeSpan constante : System.Xml.XmlConvert.ToTimeSpan, par exemple System.Xml.XmlConvert.ToTimeSpan("2004-04-15")</span><span class="sxs-lookup"><span data-stu-id="fda2b-128">For a constant TimeSpan: System.Xml.XmlConvert.ToTimeSpan, e.g System.Xml.XmlConvert.ToTimeSpan("2004-04-15")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fda2b-129">Les caractères littéraux sont exportés sous forme d'entiers non signés.</span><span class="sxs-lookup"><span data-stu-id="fda2b-129">Character literals are exported as unsigned integers.</span></span> <span data-ttu-id="fda2b-130">Par exemple, « a » est exporté en tant que 97, « b » en tant que 98 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fda2b-130">For example, 'a' is exported as 97, 'b' is exported as 98, and so forth.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fda2b-131">Les noms d'identificateur doivent respecter la spécification W3C Extensible Markup Language (XML) 1.0.</span><span class="sxs-lookup"><span data-stu-id="fda2b-131">Identifier names must conform to the W3C Extensible Markup Language (XML) 1.0 specification.</span></span>  
  
#### <a name="to-export-an-orchestration-to-bpel4ws"></a><span data-ttu-id="fda2b-132">Pour exporter une orchestration vers BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="fda2b-132">To export an orchestration to BPEL4WS</span></span>  
  
1.  <span data-ttu-id="fda2b-133">Ajoutez un nouvel élément de type Orchestration BizTalk à votre projet.</span><span class="sxs-lookup"><span data-stu-id="fda2b-133">Add a new item of type BizTalk Orchestration to your project.</span></span>  
  
2.  <span data-ttu-id="fda2b-134">Cliquez sur la surface de conception pour afficher la fenêtre Propriétés d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="fda2b-134">Click the design surface to bring up the Orchestration Properties window.</span></span>  
  
3.  <span data-ttu-id="fda2b-135">Définissez **Module Exportable** sur True.</span><span class="sxs-lookup"><span data-stu-id="fda2b-135">Set **Module Exportable** to True.</span></span>  
  
4.  <span data-ttu-id="fda2b-136">Type dans l’espace de noms pour **Module XML cible Namespace**.</span><span class="sxs-lookup"><span data-stu-id="fda2b-136">Type in the namespace you want for **Module XML Target Namespace**.</span></span>  
  
5.  <span data-ttu-id="fda2b-137">Définissez **Orchestration Exportable** sur True.</span><span class="sxs-lookup"><span data-stu-id="fda2b-137">Set **Orchestration Exportable** to True.</span></span>  
  
6.  <span data-ttu-id="fda2b-138">Type dans l’espace de noms pour **Orchestration XML cible Namespace**.</span><span class="sxs-lookup"><span data-stu-id="fda2b-138">Type in the namespace you want for **Orchestration XML Target Namespace**.</span></span>  
  
7.  <span data-ttu-id="fda2b-139">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le fichier .ODX de votre orchestration.</span><span class="sxs-lookup"><span data-stu-id="fda2b-139">In Solution Explorer, right-click the .ODX file for your orchestration.</span></span>  
  
8.  <span data-ttu-id="fda2b-140">Sélectionnez **exporter vers BPEL**.</span><span class="sxs-lookup"><span data-stu-id="fda2b-140">Select **Export to BPEL**.</span></span>  
  
     <span data-ttu-id="fda2b-141">Votre orchestration sera exportée vers BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="fda2b-141">Your orchestration will be exported to BPEL4WS.</span></span> <span data-ttu-id="fda2b-142">Consultez la fenêtre Sortie et la liste des tâches pour confirmer le succès de l’opération ou diagnostiquer des problèmes.</span><span class="sxs-lookup"><span data-stu-id="fda2b-142">See the Output Window and Task List to confirm success or diagnose problems.</span></span> <span data-ttu-id="fda2b-143">Une fois que votre exportation a réussi, un fichier .WSDL et un fichier .BPEL seront créés dans le répertoire de votre projet.</span><span class="sxs-lookup"><span data-stu-id="fda2b-143">Once your export succeeds, a .WSDL file and a .BPEL file will be created in your project directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fda2b-144">Si votre orchestration contient une assignation à un lien de rôle (lien de service) ou une assignation littérale à un port dynamique, BizTalk génère une référence à un point de terminaison BPEL4WS factice et émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fda2b-144">If your orchestration contains an assignment to a role link (service link) or a literal assignment to a dynamic port, BizTalk generates a dummy BPEL4WS endpoint reference and raises a warning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda2b-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fda2b-145">See Also</span></span>  
 <span data-ttu-id="fda2b-146">[Comment importer BPEL4WS](../core/how-to-import-bpel4ws.md) </span><span class="sxs-lookup"><span data-stu-id="fda2b-146">[How to Import BPEL4WS](../core/how-to-import-bpel4ws.md) </span></span>  
 [<span data-ttu-id="fda2b-147">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="fda2b-147">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)
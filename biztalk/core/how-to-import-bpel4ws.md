---
title: Comment importer BPEL4WS | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL4WS, restrictions
- BPEL4WS, importing
- BPEL4WS, orchestrations
- orchestrations, BPEL4WS
ms.assetid: 3626fcb9-8e7d-4812-a0c9-bde6e7954ec8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b32a0044321ce6ac57d7bd49c14b40ba17430db
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-import-bpel4ws"></a><span data-ttu-id="7aa64-102">Comment importer BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="7aa64-102">How to Import BPEL4WS</span></span>
<span data-ttu-id="7aa64-103">Vous pouvez importer un BPEL4WS existant pour créer une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7aa64-103">You can import from existing BPEL4WS to create an orchestration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7aa64-104">Cette version de BizTalk Server est compatible avec BPEL4WS 1.1.</span><span class="sxs-lookup"><span data-stu-id="7aa64-104">This release of BizTalk Server supports BPEL4WS 1.1.</span></span> <span data-ttu-id="7aa64-105">Vous ne pouvez pas importer ni exporter BPEL4WS 1.0.</span><span class="sxs-lookup"><span data-stu-id="7aa64-105">You cannot import or export BPEL4WS 1.0.</span></span>  
  
 <span data-ttu-id="7aa64-106">Pour obtenir un exemple d’importation de BPEL4WS, consultez [BPEL importer (exemple BizTalk Server)](../core/bpel-import-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7aa64-106">For an example of how to import BPEL4WS, see [BPEL Import (BizTalk Server Sample)](../core/bpel-import-biztalk-server-sample.md).</span></span>  
  
### <a name="to-import-bpel4ws-into-an-orchestration"></a><span data-ttu-id="7aa64-107">Pour importer BPEL4WS dans une orchestration</span><span class="sxs-lookup"><span data-stu-id="7aa64-107">To import BPEL4WS into an orchestration</span></span>  
  
1.  <span data-ttu-id="7aa64-108">Créez un projet.</span><span class="sxs-lookup"><span data-stu-id="7aa64-108">Create a new project.</span></span>  
  
2.  <span data-ttu-id="7aa64-109">Dans les types de projets BizTalk, double-cliquez sur Projet d'importation BPEL BizTalk Server, ou sélectionnez Projet d'importation BPEL BizTalk Server, puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="7aa64-109">From the BizTalk Project types, double-click BizTalk Server BPEL Import Project, or select BizTalk Server BPEL Import Project and press OK.</span></span>  
  
3.  <span data-ttu-id="7aa64-110">Dans l'Assistant, sélectionnez les fichiers BPEL, WSDL et XSD qui doivent être importés pour former le nouveau projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7aa64-110">In the wizard, select the BPEL, WSDL and XSD files that should be imported to form the new BizTalk project.</span></span> <span data-ttu-id="7aa64-111">Insérez tous les fichiers référencés avec les instructions importer/inclure.</span><span class="sxs-lookup"><span data-stu-id="7aa64-111">Include all files that are referenced via import and include statements.</span></span>  
  
4.  <span data-ttu-id="7aa64-112">Sélectionnez les fichiers WSDL pour les services Web appelés.</span><span class="sxs-lookup"><span data-stu-id="7aa64-112">Select WSDL files for invoked Web services.</span></span>  
  
     <span data-ttu-id="7aa64-113">Vous pouvez maintenant modifier ou déployer la nouvelle orchestration.</span><span class="sxs-lookup"><span data-stu-id="7aa64-113">You can now modify or deploy the new orchestration.</span></span>  
  
 <span data-ttu-id="7aa64-114">**Restrictions à l’importation de BPEL4WS**</span><span class="sxs-lookup"><span data-stu-id="7aa64-114">**Import restrictions on BPEL4WS**</span></span>  
  
-   <span data-ttu-id="7aa64-115">Lorsque vous importez BPEL et WSDL, vérifiez que la propriété Nom du nœud de définition WSDL et le nœud de processus BPEL ne sont pas les mêmes.</span><span class="sxs-lookup"><span data-stu-id="7aa64-115">When importing BPEL and WSDL, make sure that the Name property of the WSDL definition node and the BPEL process node do not match.</span></span>  
  
-   <span data-ttu-id="7aa64-116">N'utilisez pas de mots réservés XLANG/s dans le BPEL4WS que vous importez.</span><span class="sxs-lookup"><span data-stu-id="7aa64-116">Do not use XLANG/s reserved words in BPEL4WS that you import.</span></span> <span data-ttu-id="7aa64-117">Pour obtenir la liste complète, consultez [les mots réservés XLANG/s](../core/xlang-s-reserved-words.md).</span><span class="sxs-lookup"><span data-stu-id="7aa64-117">For a complete list, see [XLANG/s Reserved Words](../core/xlang-s-reserved-words.md).</span></span>  
  
-   <span data-ttu-id="7aa64-118">Seuls les types XSD prédéfinis simples sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7aa64-118">Only XSD predefined simple types are supported.</span></span>  
  
-   <span data-ttu-id="7aa64-119">XSD : QName n’est pas prise en charge ; Il est importé en tant que System.String.</span><span class="sxs-lookup"><span data-stu-id="7aa64-119">xsd:QName is not supported; it is imported as System.String.</span></span> <span data-ttu-id="7aa64-120">Utilisez xsd : String à la place.</span><span class="sxs-lookup"><span data-stu-id="7aa64-120">Use xsd:string instead.</span></span>  
  
-   <span data-ttu-id="7aa64-121">Pensez à utiliser des XPath canoniques lorsque vous importez BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="7aa64-121">Consider using canonical XPaths when importing BPEL4WS.</span></span>  
  
     <span data-ttu-id="7aa64-122">Pour obtenir des performances optimales, il est conseillé de n’importer que des XPath canoniques.</span><span class="sxs-lookup"><span data-stu-id="7aa64-122">It is good practice to import only canonical XPaths in order to achieve optimal performance.</span></span> <span data-ttu-id="7aa64-123">Le chemin d'accès complet de la racine au nœud promu doit être développé en utilisant '/\* [local-name()="someName" and namespace-uri()="someUri"]'.</span><span class="sxs-lookup"><span data-stu-id="7aa64-123">The entire path from root to the promoted node must be spelled out by using '/\*[local-name()="someName" and namespace-uri()="someUri"]'.</span></span>  
  
     <span data-ttu-id="7aa64-124">Si vous importez un XPath non canonique, vous pouvez supprimer une promotion et promouvoir à nouveau le même champ pour que l'Éditeur de schémas puisse créer le XPath canonique correct.</span><span class="sxs-lookup"><span data-stu-id="7aa64-124">If you import a non-canonical XPath, you can remove a promotion and repromote the same field in order to have the Schema Editor create the correct canonical XPath.</span></span>  
  
     <span data-ttu-id="7aa64-125">Exemple : (targetNamespace = http://BizTalk_Server_Project3.Schema1)</span><span class="sxs-lookup"><span data-stu-id="7aa64-125">Example: (targetNamespace = http://BizTalk_Server_Project3.Schema1)</span></span>  
  
    ```  
    <element name=Root type=complexType>  
                <sequence>  
                            <element name=promotedField/>  
                </sequence>  
    </element>  
    ```  
  
     <span data-ttu-id="7aa64-126">XPath : / * [local-name () = « Root » et namespace-uri() ='http://BizTalk_Server_Project3.Schema1'] /\*[local-name () = 'promotedField' et namespace-uri() ='']</span><span class="sxs-lookup"><span data-stu-id="7aa64-126">XPath - /*[local-name()='Root' and namespace-uri()='http://BizTalk_Server_Project3.Schema1']/\*[local-name()='promotedField' and namespace-uri()='']</span></span>  
  
    |<span data-ttu-id="7aa64-127">XPath canonique</span><span class="sxs-lookup"><span data-stu-id="7aa64-127">Canonical XPath</span></span>|<span data-ttu-id="7aa64-128">XPath non canonique</span><span class="sxs-lookup"><span data-stu-id="7aa64-128">Non-Canonical XPath</span></span>|  
    |---------------------|--------------------------|  
    |<span data-ttu-id="7aa64-129">L’Éditeur BizTalk affiche une icône spéciale (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) pour indiquer que le champ a été promu.</span><span class="sxs-lookup"><span data-stu-id="7aa64-129">BizTalk Editor displays a special icon (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) to denote that the field has been promoted.</span></span> <span data-ttu-id="7aa64-130">L’utilisation d'expressions XPath canoniques pour la promotion des champs permet d’améliorer les performances grâce à un parcours plus efficace de XML.</span><span class="sxs-lookup"><span data-stu-id="7aa64-130">Usage of canonical XPath expressions to promote fields improves performance through more efficient traversal of the XML</span></span>|<span data-ttu-id="7aa64-131">L’Éditeur BizTalk n'affiche pas d’icône spéciale.</span><span class="sxs-lookup"><span data-stu-id="7aa64-131">BizTalk Editor does not display a special icon.</span></span> <span data-ttu-id="7aa64-132">Le compilateur et la boîte de dialogue de promotion émettent des avertissements.</span><span class="sxs-lookup"><span data-stu-id="7aa64-132">Both the compiler and the promotion dialog give warnings.</span></span> <span data-ttu-id="7aa64-133">Il se produit un effet linéaire mais non trivial sur les performances à mesure que la taille des messages augmente.</span><span class="sxs-lookup"><span data-stu-id="7aa64-133">There is a linear but nontrivial effect on performance as the message size increases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7aa64-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa64-134">See Also</span></span>  
 <span data-ttu-id="7aa64-135">[Comment exporter BPEL4WS](../core/how-to-export-bpel4ws.md) </span><span class="sxs-lookup"><span data-stu-id="7aa64-135">[How to Export BPEL4WS](../core/how-to-export-bpel4ws.md) </span></span>  
 [<span data-ttu-id="7aa64-136">Conversions de types XLANG/s en BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="7aa64-136">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)
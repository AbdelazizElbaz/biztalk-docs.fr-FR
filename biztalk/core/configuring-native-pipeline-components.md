---
title: Configuration des composants de Pipeline natifs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Pipeline Designer, pipeline components
- pipeline components, configuring
- Pipeline Designer, code sample
- IPersistPropertyBag interface
ms.assetid: a3332a60-8cd6-43fa-9ecf-e1e54e71fef7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94475334395f8c360bbb636cfa9cbadcf3bf4fe3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-native-pipeline-components"></a><span data-ttu-id="4267a-102">Paramétrage des composants de pipeline natifs</span><span class="sxs-lookup"><span data-stu-id="4267a-102">Configuring Native Pipeline Components</span></span>
<span data-ttu-id="4267a-103">Les composants de pipeline peuvent présenter leurs propres propriétés personnalisées au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="4267a-103">Pipeline components can expose their own custom properties at design time.</span></span> <span data-ttu-id="4267a-104">Toute propriété publique définie dans le composant sera rendue dans le Concepteur de pipeline, à condition que des accesseurs en lecture et en écriture soient implémentés pour cette propriété.</span><span class="sxs-lookup"><span data-stu-id="4267a-104">Any public property defined in the component will be rendered in Pipeline Designer providing that read and write accessors for that property are implemented.</span></span> <span data-ttu-id="4267a-105">Le Concepteur de pipeline affiche les propriétés de composant conformément à leur déclaration ; par exemple, si la propriété est déclarée comme étant en lecture seule, elle sera affichée en tant que telle dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="4267a-105">Pipeline Designer will display the component properties in accordance with their declaration; for example, if the property is declared as read-only, it will be displayed as such in Pipeline Designer.</span></span>  
  
 <span data-ttu-id="4267a-106">Composants de pipeline personnalisés doivent implémenter le **IPersistPropertyBag** interface pour permettre la création de ces propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="4267a-106">Custom pipeline components must implement the **IPersistPropertyBag** interface to enable the creation of these custom properties.</span></span> <span data-ttu-id="4267a-107">Les propriétés créées avec le **IPersistPropertyBag** interface peut être définie dans la fenêtre Propriétés de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], à l’instar de toutes les propriétés des composants de pipeline natifs.</span><span class="sxs-lookup"><span data-stu-id="4267a-107">Properties created with the **IPersistPropertyBag** interface can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], just like all the properties of the native pipeline components.</span></span> <span data-ttu-id="4267a-108">Cette section contient les procédures de configuration de chacun des composants de pipeline inclus.</span><span class="sxs-lookup"><span data-stu-id="4267a-108">This section contains procedures for configuring each of the included pipeline components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4267a-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4267a-109">In This Section</span></span>  
  
-   [<span data-ttu-id="4267a-110">Comment configurer les composants de Pipeline natifs</span><span class="sxs-lookup"><span data-stu-id="4267a-110">How to Configure Native Pipeline Components</span></span>](../core/how-to-configure-native-pipeline-components.md)  
  
-   [<span data-ttu-id="4267a-111">Comment configurer le composant de Pipeline assembleur BizTalk Framework</span><span class="sxs-lookup"><span data-stu-id="4267a-111">How to Configure the BizTalk Framework Assembler Pipeline Component</span></span>](../core/how-to-configure-the-biztalk-framework-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-112">Comment configurer le composant de Pipeline Désassembleur BizTalk Framework</span><span class="sxs-lookup"><span data-stu-id="4267a-112">How to Configure the BizTalk Framework Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-biztalk-framework-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-113">Propriétés et schéma BizTalk Framework</span><span class="sxs-lookup"><span data-stu-id="4267a-113">BizTalk Framework Schema and Properties</span></span>](../core/biztalk-framework-schema-and-properties.md)  
  
-   [<span data-ttu-id="4267a-114">Comment configurer le composant de Pipeline d’assembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="4267a-114">How to Configure the Flat File Assembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-115">Comment configurer le composant de Pipeline de désassembleur de fichier plat</span><span class="sxs-lookup"><span data-stu-id="4267a-115">How to Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-116">Comment configurer le composant de Pipeline décodeur MIME-SMIME</span><span class="sxs-lookup"><span data-stu-id="4267a-116">How to Configure the MIME-SMIME Decoder Pipeline Component</span></span>](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-117">Configuration du composant de pipeline Encodeur MIME/SMIME</span><span class="sxs-lookup"><span data-stu-id="4267a-117">How to Configure the MIME-SMIME Encoder Pipeline Component</span></span>](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-118">Propriétés et schéma de propriété MIME-SMIME</span><span class="sxs-lookup"><span data-stu-id="4267a-118">MIME-SMIME Property Schema and Properties</span></span>](../core/mime-smime-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="4267a-119">Comment configurer le composant de Pipeline résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="4267a-119">How to Configure the Party Resolution Pipeline Component</span></span>](../core/how-to-configure-the-party-resolution-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-120">Comment configurer le composant de Pipeline assembleur XML</span><span class="sxs-lookup"><span data-stu-id="4267a-120">How to Configure the XML Assembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-121">Comment configurer le composant de Pipeline désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="4267a-121">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)  
  
-   [<span data-ttu-id="4267a-122">Propriétés et schéma de propriété de fichier plat et XML</span><span class="sxs-lookup"><span data-stu-id="4267a-122">XML and Flat File Property Schema and Properties</span></span>](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
-   [<span data-ttu-id="4267a-123">Comment configurer le composant de Pipeline valideur XML</span><span class="sxs-lookup"><span data-stu-id="4267a-123">How to Configure the XML Validator Pipeline Component</span></span>](../core/how-to-configure-the-xml-validator-pipeline-component.md)
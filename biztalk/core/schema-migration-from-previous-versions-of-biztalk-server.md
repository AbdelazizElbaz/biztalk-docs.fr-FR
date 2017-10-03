---
title: "Migration de schéma à partir de Versions précédentes de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdc86401-2002-40b8-a919-2c00cf42b557
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1666e7cc8459fd4418e0ba0963caf5b654975805
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-migration-from-previous-versions-of-biztalk-server"></a><span data-ttu-id="79ea5-102">Migration de schéma depuis des versions précédentes de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="79ea5-102">Schema Migration from Previous Versions of BizTalk Server</span></span>
<span data-ttu-id="79ea5-103">Pour représenter des schémas de message, cette version de BizTalk Server utilise le langage XSD (XML Schema Definition) et non plus la syntaxe XDR (XML-Data Reduced) comme c'était le cas des versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="79ea5-103">This version of BizTalk Server uses XML Schema definition (XSD) language to represent message schemas, while previous versions used the XML-Data Reduced (XDR) syntax to represent message schemas.</span></span> <span data-ttu-id="79ea5-104">Si vous migrez depuis une version précédente de BizTalk Server, vous devez convertir vos schémas de façon à ce qu'ils utilisent XSD au lieu d'XDR.</span><span class="sxs-lookup"><span data-stu-id="79ea5-104">If you are migrating from a previous version of BizTalk Server, you must convert your schemas to use XSD rather than XDR.</span></span>  
  
 <span data-ttu-id="79ea5-105">Vous devez effectuer les tâches suivantes pour convertir la syntaxe XDR d'un schéma BizTalk en syntaxe XSD :</span><span class="sxs-lookup"><span data-stu-id="79ea5-105">You need to perform the following tasks to convert a BizTalk schema from XDR syntax to XSD syntax:</span></span>  
  
-   <span data-ttu-id="79ea5-106">Remplacez l'extension du fichier du schéma .xsd par .xdr.</span><span class="sxs-lookup"><span data-stu-id="79ea5-106">Change the extension of the schema file from.xdr to.xsd.</span></span>  
  
-   <span data-ttu-id="79ea5-107">Ajoutez le schéma renommé au projet BizTalk approprié.</span><span class="sxs-lookup"><span data-stu-id="79ea5-107">Add the renamed schema to the appropriate BizTalk project.</span></span>  
  
-   <span data-ttu-id="79ea5-108">Convertissez le schéma renommé de XDR en XSD en l'ouvrant dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="79ea5-108">Convert the renamed schema from XDR to XSD by opening the schema in BizTalk Editor.</span></span>  
  
-   <span data-ttu-id="79ea5-109">Rendez la conversion permanente en enregistrant le schéma.</span><span class="sxs-lookup"><span data-stu-id="79ea5-109">Make the conversion permanent by saving the schema.</span></span>  
  
 <span data-ttu-id="79ea5-110">Pour plus d’informations sur la façon d’effectuer ces étapes, consultez [comment migrer les schémas XDR vers des schémas XSD](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="79ea5-110">For detailed information about how to perform these steps, see [How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ea5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79ea5-111">See Also</span></span>  
 <span data-ttu-id="79ea5-112">[À propos des schémas](../core/about-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="79ea5-112">[About Schemas](../core/about-schemas.md) </span></span>  
 <span data-ttu-id="79ea5-113">[Comment migrer les schémas XDR vers des schémas XSD](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="79ea5-113">[How to Migrate XDR Schemas to XSD Schemas](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md) </span></span>  
 [<span data-ttu-id="79ea5-114">Migration des enregistrements de fichier plat</span><span class="sxs-lookup"><span data-stu-id="79ea5-114">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)
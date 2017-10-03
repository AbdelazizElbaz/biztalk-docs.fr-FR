---
title: "Erreur : Échec de l’écriture du fichier de l’objet Blob de Type XML (&lt;file:---{0}&gt;). Erreur : {{1} de | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb787db4-0919-4e1b-bfe1-ba0e19a08881
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d76ff1a81045d3b764a6a26112a1efd74b284674
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---failure-writing-xml-type-blob-file-ltfile---0gt-error-1"></a><span data-ttu-id="2cb1d-103">Erreur : Échec de l’écriture du fichier de l’objet Blob de Type XML (&lt;file:---{0}&gt;).</span><span class="sxs-lookup"><span data-stu-id="2cb1d-103">Error - Failure writing XML Type Blob file (&lt;file:---{0}&gt;).</span></span> <span data-ttu-id="2cb1d-104">Erreur : {{1}</span><span class="sxs-lookup"><span data-stu-id="2cb1d-104">Error: {1}</span></span>
<span data-ttu-id="2cb1d-105">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="2cb1d-105">**Error Code**</span></span>  
  
 <span data-ttu-id="2cb1d-106">btm1062</span><span class="sxs-lookup"><span data-stu-id="2cb1d-106">btm1062</span></span>  
  
 <span data-ttu-id="2cb1d-107">**Explication**</span><span class="sxs-lookup"><span data-stu-id="2cb1d-107">**Explanation**</span></span>  
  
 <span data-ttu-id="2cb1d-108">Ceci se produit lorsque le compilateur du mappeur n'est pas en mesure de créer le fichier blob xml dans l'emplacement spécifié par la tâche de génération.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-108">This occurs when mapper compiler is not able to create the xml blob file in the location specified by the build task.</span></span>  
  
 <span data-ttu-id="2cb1d-109">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="2cb1d-109">**User Action**</span></span>  
  
 <span data-ttu-id="2cb1d-110">Vérifiez le message d’erreur inclus dans le message (erreur {1})i.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-110">Check the error message included in the message (Error {1})i.</span></span> <span data-ttu-id="2cb1d-111">S’il est une exception non autorisée, vous pouvez avoir pas d’autorisation en écriture pour le dossier de sortie du projet.</span><span class="sxs-lookup"><span data-stu-id="2cb1d-111">If it is an UnAuthorised exception, then you may not have write permission for the project output folder.</span></span>
---
title: "Vérification du déploiement Setup1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLASSPATH, verifying
- deployment, verifying setup
ms.assetid: 6c719e4c-9a61-480f-a4e4-0a1c518d1364
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5799d164dc2470236c3ab0286e38d19986a4d5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="verifying-the-deployment-setup"></a><span data-ttu-id="0b133-102">Vérification de la configuration du déploiement</span><span class="sxs-lookup"><span data-stu-id="0b133-102">Verifying the Deployment Setup</span></span>
<span data-ttu-id="0b133-103">Avant d'utiliser le serveur BizTalk pour importer un fichier de liaison, vous devez vérifier les éléments suivants se réalisent :</span><span class="sxs-lookup"><span data-stu-id="0b133-103">Before you use the BizTalk Server to import a binding file, you must verify the following:</span></span>  
  
-   <span data-ttu-id="0b133-104">CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="0b133-104">The CLASSPATH is pointing to a specific location for the JD Edwards EnterpriseOne-specific files.</span></span> <span data-ttu-id="0b133-105">Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="0b133-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="0b133-106">Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="0b133-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="0b133-107">Les mots de passe du système JD Edwards EnterpriseOne, si cette option a été définie dans la configuration, sont enregistrés en tant que ***** dans le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="0b133-107">JD Edwards EnterpriseOne system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="0b133-108">Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations4.md).</span><span class="sxs-lookup"><span data-stu-id="0b133-108">For more information see [Deployment Limitations](../core/deployment-limitations4.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b133-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b133-109">See Also</span></span>  
 [<span data-ttu-id="0b133-110">Déploiement de Ports et assemblys</span><span class="sxs-lookup"><span data-stu-id="0b133-110">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies3.md)
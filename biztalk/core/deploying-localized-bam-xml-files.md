---
title: "Déploiement localisée des fichiers XML de l’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, unicode mapping
- unicode mapping [BAM]
ms.assetid: 8e7e3431-cd20-45db-b7f2-0df23e9df42b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3452f13569ca6a0c0bb5843995c07a15b30f4da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-localized-bam-xml-files"></a><span data-ttu-id="3534f-102">Déploiement de fichiers XML d'analyse BAM localisés</span><span class="sxs-lookup"><span data-stu-id="3534f-102">Deploying Localized BAM XML Files</span></span>
<span data-ttu-id="3534f-103">Microsoft SQL Server Analysis Services prend en charge le mappage Unicode.</span><span class="sxs-lookup"><span data-stu-id="3534f-103">Microsoft SQL Server Analysis Services supports Unicode mapping.</span></span> <span data-ttu-id="3534f-104">Le mappage Unicode de SQL Server Analysis Services et Visual Basic Unicode pose cependant des problèmes identifiés de corruption de caractères.</span><span class="sxs-lookup"><span data-stu-id="3534f-104">However, there are known character corruption issues with SQL Server Analysis Services and Visual Basic Unicode mapping.</span></span> <span data-ttu-id="3534f-105">En effet, si les paramètres régionaux ne sont pas définis sur la langue localisée appropriée au moment où la conversion ANSI-Unicode se produit, cette conversion n'est pas effectuée avec les bonnes informations régionales et une corruption de caractères a lieu.</span><span class="sxs-lookup"><span data-stu-id="3534f-105">Specifically, if the regional settings are not set to the correct localized language when the conversion from ANSI to Unicode occurs, the conversion is performed using the wrong locale information and character corruption occurs.</span></span>  
  
 <span data-ttu-id="3534f-106">Avant de pouvoir correctement déployer le fichier XML de définition d'analyse BAM qui contient des caractères localisés, vous devez basculer les paramètres régionaux de votre système sur les paramètres régionaux appropriés.</span><span class="sxs-lookup"><span data-stu-id="3534f-106">To deploy the BAM definition XML file successfully, you must switch your system locale to the correct locale before you can actually deploy a BAM definition XML file that contains localized characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3534f-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3534f-107">See Also</span></span>  
 <span data-ttu-id="3534f-108">[La gestion BAM](../core/managing-bam.md) </span><span class="sxs-lookup"><span data-stu-id="3534f-108">[Managing BAM](../core/managing-bam.md) </span></span>  
 [<span data-ttu-id="3534f-109">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="3534f-109">BAM Management Utility</span></span>](../core/bam-management-utility.md)
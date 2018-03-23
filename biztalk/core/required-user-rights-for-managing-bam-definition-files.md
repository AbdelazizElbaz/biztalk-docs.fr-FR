---
title: Droits d’utilisateur requis pour la gestion des fichiers de définition BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb4fb73f-b783-4a04-9bd6-a135b3dd2655
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5e39c86eec0cf198a5b879cbc98d29321de71dc
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="required-user-rights-for-managing-bam-definition-files"></a><span data-ttu-id="0d593-102">Droits d'utilisateur requis pour gérer les fichiers de définition BAM</span><span class="sxs-lookup"><span data-stu-id="0d593-102">Required User Rights for Managing BAM Definition Files</span></span>
<span data-ttu-id="0d593-103">Les fichiers de définition BAM peuvent être créés, gérés et consultés par les utilisateurs de n'importe quel rôle.</span><span class="sxs-lookup"><span data-stu-id="0d593-103">BAM definition files can be created, managed, and viewed by users in any role.</span></span> <span data-ttu-id="0d593-104">La gestion des fichiers de définition BAM implique leur déploiement et leur suppression ainsi que la gestion des activités, des vues, des alertes et des artefacts qui leur sont associés.</span><span class="sxs-lookup"><span data-stu-id="0d593-104">Managing BAM definition files includes deploying and removing them as well as managing the activities, views, alerts, and artifacts that are associated with the definition file.</span></span>  
  
 <span data-ttu-id="0d593-105">Il est recommandé aux administrateurs d'assurer une protection correcte des actifs, par exemple en créant des dossiers partagés à l'accès protégé par des autorisations.</span><span class="sxs-lookup"><span data-stu-id="0d593-105">Administrators should maintain proper asset protection, such as creating shared folders with appropriate access permissions.</span></span> <span data-ttu-id="0d593-106">Nous enjoignons également les utilisateurs faisant appel au complément BAM pour Excel qu'ils définissent le niveau de sécurité des macros sur « élevé ».</span><span class="sxs-lookup"><span data-stu-id="0d593-106">When using the BAM Add-In for Excel, we recommend that users set the macro security level to high.</span></span>  
  
 <span data-ttu-id="0d593-107">Aucun droit d'utilisateur n'est requis pour modifier les fichiers de définition BAM (en fonction des autorisations définies là où les fichiers de définition sont stockés).</span><span class="sxs-lookup"><span data-stu-id="0d593-107">There are no required user rights needed to modify the BAM definition files (depending on permissions set on where the definition files are stored).</span></span> <span data-ttu-id="0d593-108">Les modifications apportées aux fichiers de définition ne sont pas automatiquement appliquées à l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="0d593-108">Changes to definition files are not automatically applied to the BAM infrastructure.</span></span> <span data-ttu-id="0d593-109">Pour appliquer ces modifications, vous devez utiliser l'utilitaire de gestion de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="0d593-109">To apply the changes you must use the BAM Management utility.</span></span>  
  
 <span data-ttu-id="0d593-110">Pour vous servir de l'utilitaire de gestion de l'analyse BAM, vous devez être administrateur sur l'ordinateur sur lequel la définition BAM est appliquée, ou membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0d593-110">To use the BAM Management utility, you must be an administrator on the computer to which the BAM definition is being applied or a member of the BizTalk Server Administrators group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d593-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="0d593-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d593-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d593-112">See Also</span></span>  
 <span data-ttu-id="0d593-113">[Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="0d593-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="0d593-114">[Qu’est une définition BAM ?](../core/what-is-a-bam-definition.md) </span><span class="sxs-lookup"><span data-stu-id="0d593-114">[What Is a BAM Definition?](../core/what-is-a-bam-definition.md) </span></span>  
 [<span data-ttu-id="0d593-115">Comment déployer des définitions BAM</span><span class="sxs-lookup"><span data-stu-id="0d593-115">How to Deploy BAM Definitions</span></span>](../core/how-to-deploy-bam-definitions.md)
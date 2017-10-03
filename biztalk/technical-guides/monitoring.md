---
title: Surveillance | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7effa38f-f9f2-40b7-8d8b-fa13cf94aa4f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9c45bb70e3f92f4c85def07add4390a0451cb87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring"></a><span data-ttu-id="2eca6-102">Surveillance</span><span class="sxs-lookup"><span data-stu-id="2eca6-102">Monitoring</span></span>
<span data-ttu-id="2eca6-103">Par défaut, tous les surveillance de BizTalk Server et les tâches utilisent le compte d’action par défaut lorsqu’il en existe qu'aucun compte d’identification spécifique ne défini pour la cible dans le profil d’identification du compte d’analyse de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2eca6-103">By default, all BizTalk Server monitoring and tasks use the default action account when there is no specific Run As Account defined for the target in the Run As Profile of the BizTalk Server Monitoring Account.</span></span> <span data-ttu-id="2eca6-104">Pour configurer un compte d’identification avec l’ensemble minimal d’autorisations requis pour BizTalk Server à des fins d’analyse, les autorisations suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="2eca6-104">To configure a Run As Account with the minimum set of permissions that are required for BizTalk Server monitoring purposes, the following permissions are required:</span></span>  
  
-   <span data-ttu-id="2eca6-105">Le compte doit être membre du groupe Administrateurs intégré et le groupe utilisateurs d’analyses de performances de l’ordinateur analysé.</span><span class="sxs-lookup"><span data-stu-id="2eca6-105">The account must be a member of the monitored computer’s built-in Administrators group and Performance Monitors Users group.</span></span>  
  
-   <span data-ttu-id="2eca6-106">Le compte doit être membre du rôle SysAdmin dans l’ou les instances qui héberge les bases de données et les travaux pour le groupe BizTalk en cours d’analyse SQL.</span><span class="sxs-lookup"><span data-stu-id="2eca6-106">The account must be a member of the SysAdmin role within the SQL instance or instances hosting the databases and jobs for the BizTalk group that is being monitored.</span></span>  
  
-   <span data-ttu-id="2eca6-107">Pour que BizTalk Server à des fins d’analyse, le compte doit être une partie du groupe des opérateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2eca6-107">For BizTalk Server monitoring purposes, the account must be a part of BizTalk Operators group.</span></span>  
  
-   <span data-ttu-id="2eca6-108">Pour exécuter des tâches via la console SCOM, le compte doit être une partie du groupe d’utilisateurs d’applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2eca6-108">For running tasks through SCOM console, the account must be a part of BizTalk Application Users group.</span></span>  
  
-   <span data-ttu-id="2eca6-109">Pour effectuer des tâches d’administration, le compte doit être une partie du groupe Administrateurs de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2eca6-109">For performing administrative tasks, the account must be a part of BizTalk Administrator group.</span></span>
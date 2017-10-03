---
title: Configurer la limite maximale de connexions au serveur SAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 858ed90e-b219-43cc-ad63-ae8e1eb2159a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853a3b78b82e242750e30099f847045ff590f125
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-the-maximum-connection-limit-to-the-sap-server"></a><span data-ttu-id="be019-102">Configurer la limite maximale de connexions au serveur SAP</span><span class="sxs-lookup"><span data-stu-id="be019-102">Configure the Maximum Connection Limit to the SAP Server</span></span>
<span data-ttu-id="be019-103">Le fournisseur de données pour SAP permet aux clients de l’adaptateur contrôler le nombre maximal de connexions qui peuvent être ouverts en interne par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="be019-103">The Data Provider for SAP enables adapter clients to control the maximum number of connections that can be opened by the provider internally.</span></span> <span data-ttu-id="be019-104">Vous pouvez le contrôler en définissant la variable d’environnement CPIC_MAX_CONV.</span><span class="sxs-lookup"><span data-stu-id="be019-104">You can control this by setting the environment variable, CPIC_MAX_CONV.</span></span>  
  
 <span data-ttu-id="be019-105">Par exemple, si CPIC_MAX_CONV est définie sur n’importe quelle valeur numérique, le nombre de connexions RFC ouvert à tout moment sera inférieur ou égal à cette valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="be019-105">For example, if CPIC_MAX_CONV is set to any numerical value, the number of RFC connections opened at any time will be less than or equal to that numerical value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be019-106">La valeur numérique s’applique pour chaque serveur individuellement sous le processus/domaine d’application qui définit cette valeur.</span><span class="sxs-lookup"><span data-stu-id="be019-106">The numerical value will be applicable for every server individually under the process/appdomain which sets this value.</span></span>  
  
 <span data-ttu-id="be019-107">Par exemple, si une application à l’aide du fournisseur de données pour SAP, a défini la variable d’environnement au niveau du processus à « x » et se connecte à deux serveurs différents, A et B, puis le nombre maximal de connexions à la fois pour A et B sera « x » respectivement.</span><span class="sxs-lookup"><span data-stu-id="be019-107">For example, if an application using Data provider for SAP, has set its environment variable at process level to “x” and connects to two different servers A and B, then the maximum number of connections for both A and B will be “x” respectively.</span></span>
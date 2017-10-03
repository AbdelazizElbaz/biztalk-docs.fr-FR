---
title: "Erreur : sérialisation Native générique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.genericNativeSerialize
ms.assetid: 3728727d-7d99-432d-844e-c956cc4635e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d2eacfae17d72dbb17786a1d924cfdf14be20ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---generic-native-serialization"></a><span data-ttu-id="5534e-102">Erreur : sérialisation Native générique</span><span class="sxs-lookup"><span data-stu-id="5534e-102">Error - Generic Native Serialization</span></span>
<span data-ttu-id="5534e-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="5534e-103">**Error Code**</span></span>  
  
 <span data-ttu-id="5534e-104">btm1049</span><span class="sxs-lookup"><span data-stu-id="5534e-104">btm1049</span></span>  
  
 <span data-ttu-id="5534e-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="5534e-105">**Explanation**</span></span>  
  
 <span data-ttu-id="5534e-106">Le message de l'instance de sortie XML généré par la transformation du mappage ne peut pas être converti au format natif spécifié par le schéma de destination en raison d'une erreur inconnue.</span><span class="sxs-lookup"><span data-stu-id="5534e-106">The XML output instance message produced by the transformation specified by the map could not be converted to the native format specified by the destination schema due to an unspecified error.</span></span>  
  
 <span data-ttu-id="5534e-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="5534e-107">**User Action**</span></span>  
  
 <span data-ttu-id="5534e-108">Ouvrir le schéma de destination dans l’Éditeur BizTalk et utiliser le **valider le schéma**, **valider l’Instance**, et **générer l’Instance** commandes, disponibles lorsque vous cliquez sur un schéma dans l’Explorateur de solutions, pour isoler le problème.</span><span class="sxs-lookup"><span data-stu-id="5534e-108">Open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, to isolate the problem.</span></span>
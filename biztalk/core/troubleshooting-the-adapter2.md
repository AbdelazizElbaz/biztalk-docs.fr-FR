---
title: "Résolution des problèmes du 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wildcard characters, in send port properties
- troubleshooting adapter
- Get.xml
- send ports, using wildcards in properties
ms.assetid: e9e0408f-5a12-4f05-83a6-37dc519ae4c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991278813d2183795239d1a75c08e474b2f8159a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a><span data-ttu-id="c8e5a-102">Dépannage de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="c8e5a-102">Troubleshooting the Adapter</span></span>
<span data-ttu-id="c8e5a-103">Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="c8e5a-103">This topic contains information to help you identify and resolve issues that you might experience while you are using Microsoft BizTalk Adapter for PeopleSoft Enterprise.</span></span>  
  
## <a name="cannot-use-wildcard-characters-in-send-port-properties"></a><span data-ttu-id="c8e5a-104">Impossible d'utiliser des caractères génériques dans les propriétés de port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c8e5a-104">Cannot use wildcard characters in send port properties</span></span>  
 <span data-ttu-id="c8e5a-105">L'adaptateur BizTalk pour PeopleSoft Enterprise ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés de port d'envoi suivants :</span><span class="sxs-lookup"><span data-stu-id="c8e5a-105">BizTalk Adapter for PeopleSoft Enterprise does not support using wildcard characters in the following send port property fields:</span></span>  
  
-   <span data-ttu-id="c8e5a-106">Utilisateur</span><span class="sxs-lookup"><span data-stu-id="c8e5a-106">Username</span></span>  
  
-   <span data-ttu-id="c8e5a-107">Chemin d'accès au serveur d'applications</span><span class="sxs-lookup"><span data-stu-id="c8e5a-107">App Server Path</span></span>  
  
-   <span data-ttu-id="c8e5a-108">Java_Home</span><span class="sxs-lookup"><span data-stu-id="c8e5a-108">Java_Home</span></span>  
  
-   <span data-ttu-id="c8e5a-109">Fichiers JAR People</span><span class="sxs-lookup"><span data-stu-id="c8e5a-109">People JAR Files</span></span>  
  
## <a name="getxml-data-assigns-0001-01-01-value-for-null-dates"></a><span data-ttu-id="c8e5a-110">Les données Get.xml affectent la valeur 0001-01-01 aux dates Null</span><span class="sxs-lookup"><span data-stu-id="c8e5a-110">Get.xml data assigns 0001-01-01 value for null dates</span></span>  
 <span data-ttu-id="c8e5a-111">Get.xml affecte de manière incorrecte la valeur 0001-01-01 aux dates Null.</span><span class="sxs-lookup"><span data-stu-id="c8e5a-111">Get.xml incorrectly assigns 0001-01-01 value for null dates.</span></span> <span data-ttu-id="c8e5a-112">Vous devez utiliser l'outil Mappeur BizTalk pour remplacer la valeur 0001-01-01 par une valeur Null.</span><span class="sxs-lookup"><span data-stu-id="c8e5a-112">You must use the BizTalk Mapper tool if you want to replace the 0001-01-01 with null.</span></span>  
  
## <a name="creating-and-updating-properties-with-collections-fails"></a><span data-ttu-id="c8e5a-113">Échec de la création et de la mise à jour des propriétés avec des collections</span><span class="sxs-lookup"><span data-stu-id="c8e5a-113">Creating and updating properties with collections fails</span></span>  
 <span data-ttu-id="c8e5a-114">Lors d'une utilisation avec PeopleSoft version 8.17.02, l'adaptateur peut lire les données du serveur PeopleSoft correctement.</span><span class="sxs-lookup"><span data-stu-id="c8e5a-114">When using the Adapter with PeopleSoft version 8.17.02, the Adapter can read data from PeopleSoft server correctly.</span></span> <span data-ttu-id="c8e5a-115">Cependant, la création et la mise à jour échouent pour les propriétés avec des collections</span><span class="sxs-lookup"><span data-stu-id="c8e5a-115">However, creating and updating fails for properties with collections.</span></span> <span data-ttu-id="c8e5a-116">Il s'agit d'un problème PeopleSoft connu qui sera peut-être résolu dans une version ultérieure de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="c8e5a-116">This is a known PeopleSoft issue that may be fixed in a future release of PeopleSoft.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e5a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8e5a-117">See Also</span></span>  
 [<span data-ttu-id="c8e5a-118">Résolution des problèmes de PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="c8e5a-118">Troubleshooting PeopleSoft</span></span>](../core/troubleshooting-peoplesoft.md)
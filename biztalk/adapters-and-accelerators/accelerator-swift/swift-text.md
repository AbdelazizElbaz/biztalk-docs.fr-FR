---
title: Texte SWIFT | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT, text
ms.assetid: 90851d38-7789-4b1b-813b-7943f77ab984
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80d8ee0343cbf8ac96d57119ef198d623159b26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-text"></a><span data-ttu-id="07d9d-102">Texte SWIFT</span><span class="sxs-lookup"><span data-stu-id="07d9d-102">SWIFT Text</span></span>
<span data-ttu-id="07d9d-103">Le texte du message constitue la charge utile du message (FIN) financier et contient tous les champs de données à l’exception des champs contenant l’expéditeur, le récepteur et le type de message.</span><span class="sxs-lookup"><span data-stu-id="07d9d-103">The message text makes up the payload of the financial (FIN) message, and contains all of the data fields except the fields containing the sender, receiver, and message type.</span></span> <span data-ttu-id="07d9d-104">Ces trois champs sont contenus dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="07d9d-104">These three fields are contained in the header portion.</span></span> <span data-ttu-id="07d9d-105">Certains messages contiennent également un en-tête utilisateur facultatif, qui peuvent également fournir des informations de traitement.</span><span class="sxs-lookup"><span data-stu-id="07d9d-105">Some messages also contain an optional User Header, which may also provide processing information.</span></span>  
  
 <span data-ttu-id="07d9d-106">Chaque charge de message FIN se compose d’une série de champs dans un ordre défini.</span><span class="sxs-lookup"><span data-stu-id="07d9d-106">Each FIN message payload consists of a series of fields in a defined sequence.</span></span> <span data-ttu-id="07d9d-107">Ces champs sont conformes aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="07d9d-107">These fields conform to the following rules:</span></span>  
  
-   <span data-ttu-id="07d9d-108">Les champs peuvent être obligatoires ou facultatifs dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="07d9d-108">The fields may be required or optional within the sequence.</span></span>  
  
-   <span data-ttu-id="07d9d-109">Une séquence peut contenir sous-séquences, et une sous-séquence peut se répètent dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="07d9d-109">A sequence may contain subsequences, and a subsequence may repeat within a sequence.</span></span>  
  
-   <span data-ttu-id="07d9d-110">Vous pouvez utiliser un champ dans plusieurs types de messages.</span><span class="sxs-lookup"><span data-stu-id="07d9d-110">You can use a field in several message types.</span></span>  
  
-   <span data-ttu-id="07d9d-111">Un champ peut comporter des éléments ou sous-champs.</span><span class="sxs-lookup"><span data-stu-id="07d9d-111">Within a field, there may be elements or subfields.</span></span> <span data-ttu-id="07d9d-112">Un élément ou un sous-champ peut-être être commune à plusieurs champs.</span><span class="sxs-lookup"><span data-stu-id="07d9d-112">An element or subfield may be common to several fields.</span></span>  
  
-   <span data-ttu-id="07d9d-113">Chaque séquence répétitive est représentée par un nœud de groupe.</span><span class="sxs-lookup"><span data-stu-id="07d9d-113">Each repeating sequence is represented by a group node.</span></span>  
  
-   <span data-ttu-id="07d9d-114">Chaque champ peut lui-même avoir plusieurs noeuds niveaux, chacune décrite comme un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="07d9d-114">Each field may itself have multiple nodal levels, each described as a record.</span></span>  
  
-   <span data-ttu-id="07d9d-115">Un élément de schéma représente le sous-champ de niveau le plus bas.</span><span class="sxs-lookup"><span data-stu-id="07d9d-115">A schema element represents only the lowest level subfield.</span></span>  
  
-   <span data-ttu-id="07d9d-116">Courantes des enregistrements et des éléments sont définis dans le schéma commun et de base, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="07d9d-116">Common records and elements are defined in the common and base schema, as described below.</span></span>  
  
-   <span data-ttu-id="07d9d-117">Certains champs peuvent être représentés dans plusieurs formats (tels que les champs de tiers).</span><span class="sxs-lookup"><span data-stu-id="07d9d-117">Some fields may be represented in several formats (such as party fields).</span></span> <span data-ttu-id="07d9d-118">Ces champs sont définis en tant que champs de choix dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="07d9d-118">Such fields are defined as choice fields in the schema.</span></span>  
  
 <span data-ttu-id="07d9d-119">Certains champs ont limité des ensembles de valeurs.</span><span class="sxs-lookup"><span data-stu-id="07d9d-119">Some fields have limited sets of values.</span></span> <span data-ttu-id="07d9d-120">La plupart des cas, le schéma répertorie ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="07d9d-120">For the most part, the schema lists these values.</span></span> <span data-ttu-id="07d9d-121">Définitions de schéma également incluent la validation de jeu de caractères.</span><span class="sxs-lookup"><span data-stu-id="07d9d-121">Schema definitions also include character set validation.</span></span>
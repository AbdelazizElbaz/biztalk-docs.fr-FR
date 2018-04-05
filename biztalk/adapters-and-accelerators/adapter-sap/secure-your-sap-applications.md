---
title: Sécuriser vos applications SAP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security and protection
ms.assetid: 9f0fb2a2-d6e2-4561-8472-c0bf682a4798
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49f5fe75acf7b033d0f957c7742f52ba521bdde7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-sap-applications"></a><span data-ttu-id="1d320-102">Sécuriser vos applications SAP</span><span class="sxs-lookup"><span data-stu-id="1d320-102">Secure your SAP applications</span></span>
<span data-ttu-id="1d320-103">Le système SAP peut contenir des informations sensibles telles que les détails du compte client.</span><span class="sxs-lookup"><span data-stu-id="1d320-103">The SAP system can contain sensitive business information such as customer account details.</span></span> <span data-ttu-id="1d320-104">Les applications qui utilisent le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission.</span><span class="sxs-lookup"><span data-stu-id="1d320-104">Applications that use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="1d320-105">Sécurité et protection des données sont généralement considérées dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="1d320-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="1d320-106">*Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="1d320-106">*Authorization* controls access to a resource based on the identity of the requestor.</span></span>  
  
-   <span data-ttu-id="1d320-107">*Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.</span><span class="sxs-lookup"><span data-stu-id="1d320-107">*Authentication* provides mechanisms for verifying the identity of a requestor.</span></span>  
  
-   <span data-ttu-id="1d320-108">*La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="1d320-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="1d320-109">*L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.</span><span class="sxs-lookup"><span data-stu-id="1d320-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="1d320-110">Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d320-110">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d320-111">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="1d320-111">In this section</span></span>  
  
-   [<span data-ttu-id="1d320-112">Sécurité entre le système SAP et de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="1d320-112">Security between the SAP system and the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md)
  
-   [<span data-ttu-id="1d320-113">Sécurité avec l’adaptateur SAP et de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1d320-113">Security with the SAP adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md)
  
-   [<span data-ttu-id="1d320-114">Programmation sécurisée avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="1d320-114">Secure programming with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md)
  
-   [<span data-ttu-id="1d320-115">Meilleures pratiques pour sécuriser l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="1d320-115">Best practices to secure the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)
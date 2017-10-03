---
title: "Architecture de sécurité de l’adaptateur FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faeebd6-5287-4ac4-a1db-e3c055d323d2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ed8352b788af12fd3c38f489e9ddb65d8375f2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fileact-adapter-security-architecture"></a><span data-ttu-id="17049-102">Architecture de sécurité de l’adaptateur FileAct</span><span class="sxs-lookup"><span data-stu-id="17049-102">FileAct Adapter Security Architecture</span></span>
<span data-ttu-id="17049-103">Sécurité pour la transmission du fichier et la réception est implémentée via les fonctionnalités de certificat et de chiffrement inhérents aux SNL et les trous.</span><span class="sxs-lookup"><span data-stu-id="17049-103">Security for the file transmission and receipt is implemented using the certificate and crypto features inherent in SNL and the SAG.</span></span>  <span data-ttu-id="17049-104">La gestion des certificats, etc., est complètement hors de portée de l’adaptateur FileAct.</span><span class="sxs-lookup"><span data-stu-id="17049-104">The management of certificates, etc., is completely outside of the scope of the FileAct Adapter.</span></span> <span data-ttu-id="17049-105">Tant que l’instance associée de SNL/trous est enregistrée pour le service FileAct avec SWIFT et le logiciel installé correctement sur SNL/trous, l’adaptateur utilise le fonctionnalités via les API SNL.</span><span class="sxs-lookup"><span data-stu-id="17049-105">As long as the associated SNL/SAG instance is registered for the FileAct service with SWIFT and the software properly installed on SNL/SAG, the adapter makes use of the facilities throught the SNL APIs.</span></span> <span data-ttu-id="17049-106">L’adaptateur FileAct toujours la valeur du FACryptoMode sur « Avancé » (recommandé).</span><span class="sxs-lookup"><span data-stu-id="17049-106">The FileAct Adapter will always set the FACryptoMode to “Advanced” (best practice).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17049-107">Pour la carte, vous pouvez créer un contexte de sécurité distincts pour chaque port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="17049-107">For the adapter, you can create a separate security context for  each send port.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17049-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17049-108">See Also</span></span>  
 <span data-ttu-id="17049-109">[Architecture de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="17049-109">[FileAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="17049-110">[Primitives de bout en bout FileAct adaptateur en temps réel](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="17049-110">[FileAct Adapter Real-Time End-to-End Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-end-to-end-primitives.md) </span></span>  
 <span data-ttu-id="17049-111">[Primitives locales en temps réel de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span><span class="sxs-lookup"><span data-stu-id="17049-111">[FileAct Adapter Real-Time Local Primitives](../../adapters-and-accelerators/fileact-interact/fileact-adapter-real-time-local-primitives.md) </span></span>  
 <span data-ttu-id="17049-112">[Magasin de l’adaptateur FileAct et le transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="17049-112">[FileAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/fileact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="17049-113">[Fichier de l’adaptateur FileAct et Identification de transfert](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span><span class="sxs-lookup"><span data-stu-id="17049-113">[FileAct Adapter File and Transfer Identification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-file-and-transfer-identification.md) </span></span>  
 <span data-ttu-id="17049-114">[Transfert des informations de prise en charge de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span><span class="sxs-lookup"><span data-stu-id="17049-114">[FileAct Adapter Supporting Information Transfer](../../adapters-and-accelerators/fileact-interact/fileact-adapter-supporting-information-transfer.md) </span></span>  
 <span data-ttu-id="17049-115">[Notification de remise de l’adaptateur FileAct](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span><span class="sxs-lookup"><span data-stu-id="17049-115">[FileAct Adapter Delivery Notification](../../adapters-and-accelerators/fileact-interact/fileact-adapter-delivery-notification.md) </span></span>  
 [<span data-ttu-id="17049-116">État de l’adaptateur FileAct analyse</span><span class="sxs-lookup"><span data-stu-id="17049-116">FileAct Adapter Status Monitoring</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-status-monitoring.md)
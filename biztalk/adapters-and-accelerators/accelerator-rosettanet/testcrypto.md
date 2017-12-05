---
title: TestCrypto | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, TestCrypto utility
- troubleshooting, TestCrypto utility
- TestCrypto utility
ms.assetid: 02768794-64ac-4d99-930c-738bed9626c5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 632ad57a8bb8a32c8f579a07980480dbd3bf0087
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="testcrypto"></a><span data-ttu-id="12e54-102">TestCrypto</span><span class="sxs-lookup"><span data-stu-id="12e54-102">TestCrypto</span></span>
<span data-ttu-id="12e54-103">Vous utilisez l’utilitaire TestCrypto pour résoudre les échecs de déchiffrement des messages.</span><span class="sxs-lookup"><span data-stu-id="12e54-103">You use the TestCrypto utility to troubleshoot failures in decrypting messages.</span></span> <span data-ttu-id="12e54-104">L’utilitaire indique si le déchiffrement échoue.</span><span class="sxs-lookup"><span data-stu-id="12e54-104">The utility indicates whether decryption fails.</span></span> <span data-ttu-id="12e54-105">Si le déchiffrement réussisse, l’utilitaire indique que le certificat est et affiche le message déchiffré.</span><span class="sxs-lookup"><span data-stu-id="12e54-105">If the decryption succeeds, the utility indicates what the certificate is, and displays the decrypted message.</span></span>  
  
 <span data-ttu-id="12e54-106">Vous exécutez TestCrypto sur un fichier qui contient uniquement la partie chiffrée du message, sans les en-têtes non chiffrés.</span><span class="sxs-lookup"><span data-stu-id="12e54-106">You run TestCrypto on a file that contains only the encrypted part of the message, without unencrypted headers.</span></span> <span data-ttu-id="12e54-107">Extraire l’objet binaire volumineux (BLOB) de chiffré du message dans un fichier texte, en espionnant le message entrant ou en récupérant le message à partir de `MessageStorageIn`.</span><span class="sxs-lookup"><span data-stu-id="12e54-107">Extract the encrypted binary large object (BLOB) from the message into a text file, either by sniffing the incoming message or by retrieving the message from `MessageStorageIn`.</span></span>  
  
 <span data-ttu-id="12e54-108">Pour plus d’informations sur la récupération d’un message à partir de `MessageStorageIn`, consultez [GetMessages exemple](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md).</span><span class="sxs-lookup"><span data-stu-id="12e54-108">For more information about retrieving a message from `MessageStorageIn`, see [GetMessages Sample](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md).</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="12e54-109">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="12e54-109">Location in SDK</span></span>  
 <span data-ttu-id="12e54-110">\<*lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="12e54-110">\<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK</span></span>  
  
## <a name="running-testcrypto"></a><span data-ttu-id="12e54-111">TestCrypto en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="12e54-111">Running TestCrypto</span></span>  
  
#### <a name="to-run-testcrypto"></a><span data-ttu-id="12e54-112">Pour exécuter TestCrypto</span><span class="sxs-lookup"><span data-stu-id="12e54-112">To run TestCrypto</span></span>  
  
1.  <span data-ttu-id="12e54-113">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="12e54-113">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="12e54-114">Déplacer vers \< *lecteur*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span><span class="sxs-lookup"><span data-stu-id="12e54-114">Move to \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.</span></span>  
  
3.  <span data-ttu-id="12e54-115">À l’invite de commandes, tapez **TestCrypto.exe \<nom de fichier\>**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="12e54-115">At the command prompt, type **TestCrypto.exe \<filename\>**, and then press ENTER.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e54-116">Notes</span><span class="sxs-lookup"><span data-stu-id="12e54-116">Remarks</span></span>  
 <span data-ttu-id="12e54-117">Le déchiffrement échoue si le certificat que l’utilitaire de recherche n’est pas le certificat requis et valid, ou si l’utilitaire ne peut pas trouver le certificat.</span><span class="sxs-lookup"><span data-stu-id="12e54-117">Decryption fails if the certificate that the utility finds is not the required and valid certificate, or if the utility cannot find the certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e54-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12e54-118">See Also</span></span>  
 [<span data-ttu-id="12e54-119">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="12e54-119">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
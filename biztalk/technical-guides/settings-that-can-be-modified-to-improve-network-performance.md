---
title: "Les paramètres qui peuvent être modifiées pour améliorer les performances réseau | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb6aacc3-e697-4cc9-b937-73a2f54e733b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c4b32a5a5f588e76d155c2f8d052398f1a247
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="settings-that-can-be-modified-to-improve-network-performance"></a><span data-ttu-id="34c4f-102">Paramètres qui peuvent être modifiées pour améliorer les performances réseau</span><span class="sxs-lookup"><span data-stu-id="34c4f-102">Settings that can be Modified to Improve Network Performance</span></span>
<span data-ttu-id="34c4f-103">Cette rubrique fournit une description des valeurs recommandées cet impact sur les performances réseau.</span><span class="sxs-lookup"><span data-stu-id="34c4f-103">This topic provides a description of recommended values   that impact network performance.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34c4f-104">Pendant le test de performances s’est terminée pour ce guide, il a été observé que Windows Server 2008 semble être paramétrée par défaut.</span><span class="sxs-lookup"><span data-stu-id="34c4f-104">During performance testing completed for this guide it was observed that Windows Server 2008 appears to be tuned by default.</span></span> <span data-ttu-id="34c4f-105">Modification des paramètres de Registre doit être effectuée après une analyse approfondie des effets sur le système.</span><span class="sxs-lookup"><span data-stu-id="34c4f-105">Modification of  registry settings should only be done after a careful analysis of the effects on the system.</span></span>  
  
## <a name="adjust-the-maxuserport-and-tcptimedwaitdelay-settings"></a><span data-ttu-id="34c4f-106">Ajuster les paramètres MaxUserPort et TcpTimedWaitDelay</span><span class="sxs-lookup"><span data-stu-id="34c4f-106">Adjust the MaxUserPort and TcpTimedWaitDelay settings</span></span>  
 <span data-ttu-id="34c4f-107">Le **MaxUserPort** valeur contrôle le nombre maximal de port utilisé lorsqu’une application demande un port utilisateur disponible à partir du système.</span><span class="sxs-lookup"><span data-stu-id="34c4f-107">The **MaxUserPort** value controls the maximum port number used when an application requests any available user port from the system.</span></span> <span data-ttu-id="34c4f-108">Normalement, les ports éphémères sont alloués dans la plage de 1025 et 65535.</span><span class="sxs-lookup"><span data-stu-id="34c4f-108">Normally, short-lived ports are allocated in the range from 1025 through 65535.</span></span> <span data-ttu-id="34c4f-109">La plage de ports est désormais réellement une plage avec un point de départ et un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="34c4f-109">The port range is now truly a range with a starting point and with an endpoint.</span></span> <span data-ttu-id="34c4f-110">Le nouveau port de démarrage par défaut est 49152, et le port de fin par défaut est 65535.</span><span class="sxs-lookup"><span data-stu-id="34c4f-110">The new default start port is 49152, and the default end port is 65535.</span></span> <span data-ttu-id="34c4f-111">Cette plage est en plus des ports connus utilisés par les services et applications.</span><span class="sxs-lookup"><span data-stu-id="34c4f-111">This range is in addition to well-known ports that are used by services and by applications.</span></span> <span data-ttu-id="34c4f-112">La plage de ports utilisée par les serveurs peut être modifiée sur chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="34c4f-112">The port range that is used by the servers can be modified on each server.</span></span> <span data-ttu-id="34c4f-113">Vous réglez cette plage à l’aide de la commande netsh, comme suit :</span><span class="sxs-lookup"><span data-stu-id="34c4f-113">You adjust this range by using the netsh command, as follows:</span></span>  
  
 <span data-ttu-id="34c4f-114">**netsh int \<ipv4 &#124; ipv6 > définir dynamiques \<tcp &#124; udp > Démarrer = nombre num = plage**</span><span class="sxs-lookup"><span data-stu-id="34c4f-114">**netsh int \<ipv4&#124;ipv6> set dynamicport \<tcp&#124;udp> start=number num=range**</span></span>  
  
 <span data-ttu-id="34c4f-115">Cette commande définit la plage de ports dynamiques TCP.</span><span class="sxs-lookup"><span data-stu-id="34c4f-115">This command sets the dynamic port range for TCP.</span></span> <span data-ttu-id="34c4f-116">Le port de début est **nombre**, et le nombre total de ports est **plage**.</span><span class="sxs-lookup"><span data-stu-id="34c4f-116">The start port is **number**, and the total number of ports is **range**.</span></span> <span data-ttu-id="34c4f-117">Voici des exemples de commandes : vous pouvez afficher la plage de ports dynamiques en utilisant les commandes netsh suivantes :</span><span class="sxs-lookup"><span data-stu-id="34c4f-117">The following are sample commands: You can view the dynamic port range by using the following netsh commands:</span></span>  
  
-   <span data-ttu-id="34c4f-118">netsh int ipv4 afficher dynamiques tcp.</span><span class="sxs-lookup"><span data-stu-id="34c4f-118">netsh int ipv4 show dynamicport tcp.</span></span> <span data-ttu-id="34c4f-119">Pour augmenter la plage à la valeur maximale autorisée pour le tcp v4, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="34c4f-119">To increase the range to the maximum allowed value for tcp v4, use the following command:</span></span>  
  
     <span data-ttu-id="34c4f-120">**netsh int ipv4 définir dynamiques tcp start = 1025 num = 64511**</span><span class="sxs-lookup"><span data-stu-id="34c4f-120">**netsh int ipv4 set dynamicport tcp start=1025 num=64511**</span></span>  
  
-   <span data-ttu-id="34c4f-121">netsh int ipv4 afficher dynamiques udp</span><span class="sxs-lookup"><span data-stu-id="34c4f-121">netsh int ipv4 show dynamicport udp</span></span>  
  
-   <span data-ttu-id="34c4f-122">netsh int ipv6 afficher dynamiques tcp</span><span class="sxs-lookup"><span data-stu-id="34c4f-122">netsh int ipv6 show dynamicport tcp</span></span>  
  
-   <span data-ttu-id="34c4f-123">netsh int ipv6 afficher dynamiques udp</span><span class="sxs-lookup"><span data-stu-id="34c4f-123">netsh int ipv6 show dynamicport udp</span></span>  
  
 <span data-ttu-id="34c4f-124">Le **TcpTimedWaitDelay** valeur détermine la durée pendant laquelle une connexion reste dans l’état TIME_WAIT lors de la fermeture.</span><span class="sxs-lookup"><span data-stu-id="34c4f-124">The **TcpTimedWaitDelay** value determines the length of time that a connection stays in the TIME_WAIT state when being closed.</span></span> <span data-ttu-id="34c4f-125">Lorsqu’une connexion est dans l’état TIME_WAIT, la paire de sockets ne peut pas être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="34c4f-125">While a connection is in the TIME_WAIT state, the socket pair cannot be reused.</span></span> <span data-ttu-id="34c4f-126">Cela est également appelé l’état 2MSL car la valeur doit être deux fois la durée de vie maximale de segment sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="34c4f-126">This is also known as the 2MSL state because the value should be twice the maximum segment lifetime on the network.</span></span> <span data-ttu-id="34c4f-127">Pour plus d’informations, consultez [Internet RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=113719 » http://go.microsoft.com/fwlink/?LinkId=113719).</span><span class="sxs-lookup"><span data-stu-id="34c4f-127">For more information, see [Internet RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) ( HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=113719" http://go.microsoft.com/fwlink/?LinkId=113719).</span></span> <span data-ttu-id="34c4f-128">Pour ajuster les paramètres de TcpTimedWaitDelay, vous devez modifier les paramètres du Registre comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="34c4f-128">To adjust the TcpTimedWaitDelay settings, you have to modify the registry settings as listed below:</span></span>  
  
###  
  
|||  
|-|-|  
|<span data-ttu-id="34c4f-129">Clé :</span><span class="sxs-lookup"><span data-stu-id="34c4f-129">Key:</span></span>|<span data-ttu-id="34c4f-130">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters</span><span class="sxs-lookup"><span data-stu-id="34c4f-130">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters</span></span>|  
|<span data-ttu-id="34c4f-131">Valeur :</span><span class="sxs-lookup"><span data-stu-id="34c4f-131">Value:</span></span>|<span data-ttu-id="34c4f-132">TcpTimedWaitDelay</span><span class="sxs-lookup"><span data-stu-id="34c4f-132">TcpTimedWaitDelay</span></span>|  
|<span data-ttu-id="34c4f-133">Type de données :</span><span class="sxs-lookup"><span data-stu-id="34c4f-133">Data Type:</span></span>|<span data-ttu-id="34c4f-134">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="34c4f-134">REG_DWORD</span></span>|  
|<span data-ttu-id="34c4f-135">Plage :</span><span class="sxs-lookup"><span data-stu-id="34c4f-135">Range:</span></span>|<span data-ttu-id="34c4f-136">30-300 (décimal)</span><span class="sxs-lookup"><span data-stu-id="34c4f-136">30-300 (decimal)</span></span>|  
|<span data-ttu-id="34c4f-137">Valeur par défaut :</span><span class="sxs-lookup"><span data-stu-id="34c4f-137">Default value:</span></span>|<span data-ttu-id="34c4f-138">0 x 78 (120 valeur décimale)</span><span class="sxs-lookup"><span data-stu-id="34c4f-138">0x78 (120 decimal)</span></span>|  
|<span data-ttu-id="34c4f-139">Valeur recommandée :</span><span class="sxs-lookup"><span data-stu-id="34c4f-139">Recommended value:</span></span>|<span data-ttu-id="34c4f-140">30</span><span class="sxs-lookup"><span data-stu-id="34c4f-140">30</span></span>|  
|<span data-ttu-id="34c4f-141">Il existe une valeur par défaut ?</span><span class="sxs-lookup"><span data-stu-id="34c4f-141">Value exists by default?</span></span>|<span data-ttu-id="34c4f-142">**Ne**, doit être ajouté.</span><span class="sxs-lookup"><span data-stu-id="34c4f-142">**No**, needs to be added.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34c4f-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34c4f-143">See Also</span></span>  
 [<span data-ttu-id="34c4f-144">Instructions générales pour améliorer les performances du réseau</span><span class="sxs-lookup"><span data-stu-id="34c4f-144">General Guidelines for Improving Network Performance</span></span>](../technical-guides/general-guidelines-for-improving-network-performance.md)
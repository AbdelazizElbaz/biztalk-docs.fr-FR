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
# <a name="settings-that-can-be-modified-to-improve-network-performance"></a>Paramètres qui peuvent être modifiées pour améliorer les performances réseau
Cette rubrique fournit une description des valeurs recommandées cet impact sur les performances réseau.  
  
> [!IMPORTANT]  
>  Pendant le test de performances s’est terminée pour ce guide, il a été observé que Windows Server 2008 semble être paramétrée par défaut. Modification des paramètres de Registre doit être effectuée après une analyse approfondie des effets sur le système.  
  
## <a name="adjust-the-maxuserport-and-tcptimedwaitdelay-settings"></a>Ajuster les paramètres MaxUserPort et TcpTimedWaitDelay  
 Le **MaxUserPort** valeur contrôle le nombre maximal de port utilisé lorsqu’une application demande un port utilisateur disponible à partir du système. Normalement, les ports éphémères sont alloués dans la plage de 1025 et 65535. La plage de ports est désormais réellement une plage avec un point de départ et un point de terminaison. Le nouveau port de démarrage par défaut est 49152, et le port de fin par défaut est 65535. Cette plage est en plus des ports connus utilisés par les services et applications. La plage de ports utilisée par les serveurs peut être modifiée sur chaque serveur. Vous réglez cette plage à l’aide de la commande netsh, comme suit :  
  
 **netsh int \<ipv4 &#124; ipv6 > définir dynamiques \<tcp &#124; udp > Démarrer = nombre num = plage**  
  
 Cette commande définit la plage de ports dynamiques TCP. Le port de début est **nombre**, et le nombre total de ports est **plage**. Voici des exemples de commandes : vous pouvez afficher la plage de ports dynamiques en utilisant les commandes netsh suivantes :  
  
-   netsh int ipv4 afficher dynamiques tcp. Pour augmenter la plage à la valeur maximale autorisée pour le tcp v4, utilisez la commande suivante :  
  
     **netsh int ipv4 définir dynamiques tcp start = 1025 num = 64511**  
  
-   netsh int ipv4 afficher dynamiques udp  
  
-   netsh int ipv6 afficher dynamiques tcp  
  
-   netsh int ipv6 afficher dynamiques udp  
  
 Le **TcpTimedWaitDelay** valeur détermine la durée pendant laquelle une connexion reste dans l’état TIME_WAIT lors de la fermeture. Lorsqu’une connexion est dans l’état TIME_WAIT, la paire de sockets ne peut pas être réutilisée. Cela est également appelé l’état 2MSL car la valeur doit être deux fois la durée de vie maximale de segment sur le réseau. Pour plus d’informations, consultez [Internet RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=113719 » http://go.microsoft.com/fwlink/?LinkId=113719). Pour ajuster les paramètres de TcpTimedWaitDelay, vous devez modifier les paramètres du Registre comme indiqué ci-dessous :  
  
###  
  
|||  
|-|-|  
|Clé :|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters|  
|Valeur :|TcpTimedWaitDelay|  
|Type de données :|REG_DWORD|  
|Plage :|30-300 (décimal)|  
|Valeur par défaut :|0 x 78 (120 valeur décimale)|  
|Valeur recommandée :|30|  
|Il existe une valeur par défaut ?|**Ne**, doit être ajouté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions générales pour améliorer les performances du réseau](../technical-guides/general-guidelines-for-improving-network-performance.md)
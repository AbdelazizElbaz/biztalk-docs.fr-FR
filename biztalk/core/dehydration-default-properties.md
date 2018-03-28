---
title: Propriétés par défaut de mise en attente | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68c59def-d73b-4880-9884-ccbe5d982f4b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff78b1e096f1a73675ffc02550794f5a300f5614
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="dehydration-default-properties"></a>Propriétés par défaut de mise en attente
Vous trouverez ci-après les noms des propriétés de mise en attente et leurs valeurs par défaut. Ces propriétés peuvent être configurées dans le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] ou dans le code XML du fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config). Les valeurs contenues dans le fichier de configuration de BizTalk sont appliquées en premier. Les paramètres du [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] sont ensuite appliqués. Les propriétés de mise en attente sont lues lorsque toutes les instances de l’hôte contenant une orchestration démarrent.  
  
> [!IMPORTANT]
>  Tous les paramètres d’orchestration ne sont pas exposés dans le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]. Pour ces paramètres, le fichier de configuration de BizTalk (BTSNTSvc.exe.config ou BTSNTSvc64.exe.config) est utilisé. Lors de l’utilisation du fichier de configuration de BizTalk, de nombreuses propriétés ne sont pas répertoriées. Ces propriétés et leurs valeurs par défaut sont toujours appliquées, même si elles ne sont pas explicitement spécifiées dans le fichier de configuration.  
  
 Pour modifier les valeurs par défaut, vous pouvez utiliser le [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] ou les ajouter explicitement au fichier de configuration de BizTalk. Pour plus d’informations, consultez [à l’aide de paramètres de tableau de bord pour BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) et [fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md).  
  
 **Mise en attente**  
  
-   **MaxThreshold** = 1800  
  
-   **MinThreshold** = 1  
  
-   **ConstantThreshold** = -1  
  
 **VirtualMemoryThrottlingCriteria**  
  
-   **OptimalUsage** = 900  
  
-   **MaximalUsage** = 1300  
  
-   **IsActive** = true  
  
 **PrivateMemoryThrottlingCriteria**  
  
-   **OptimalUsage** = 50  
  
-   **MaximalUsage** = 350  
  
-   **IsActive** = true  
  
 **PhysicalMemoryThrottlingCriteria**  
  
-   **OptimalUsage** = 90  
  
-   **MaximalUsage** = 95  
  
-   **IsActive** = false  
  
 Chacune de ces propriétés est décrite en détail par la suite.  
  
## <a name="dehydration"></a>Mise en attente  
 **MaxThreshold** et **MinThreshold** sont la limite supérieure et inférieure limites, en secondes, de l’heure à laquelle une orchestration peut être bloquée au niveau d’un abonnement (c'est-à-dire bloqué par une réception, écouter ou délai) avant d’être mise en attente. Il y aura également une valeur calculée au moment de l’exécution, appelée **TestThreshold**, et sa valeur, exprimée en secondes, entre **MinThreshold** et **MaxThreshold**.  
  
 Si vous définissez une valeur par défaut de -1 pour **ConstantThreshold**, il y aura pas d’une valeur d’exécution **TestThreshold**. Lorsqu’une orchestration est bloquée au niveau d’un abonnement, et l’historique de la durée pendant laquelle toutes les instances de cette orchestration ont été bloqués à cet abonnement est supérieure à la valeur de **TestThreshold**, puis l’orchestration sera mise en attente. Sinon, si l’historique est inférieure à **TestThreshold** valeur l’orchestration n’est pas mise en attente. En outre, même si l’historique indique que la mise en attente n’aura pas lieu, si la durée de blocage actuelle atteint 2 ***TestThreshold**, puis la mise en attente a lieu. L'historique est défini par la moyenne des 10 derniers délais d'attente (en secondes) ou la moyenne des délais d'attente contenus dans l'historique si leur nombre est inférieur à 10.  
  
 Lorsque la valeur de **TestThreshold** tend vers **MinThreshold** en tant que l’utilisation de la mémoire augmente, elle est appelée « mémoire limitation basée sur la mise en attente. » Cette limitation permet de conserver un nombre plus important d’instances d’orchestration actives, car dès que l’une d’entre elles est bloquée en attente de travaux (à savoir, en attente d’un message ou d’un délai), elle peut être mise en attente et retirée de la mémoire. **TestThreshold** est une fonction décroissante de l’utilisation de la mémoire, il est inversement proportionnelle à l’utilisation de la mémoire.  
  
 Voici les descriptions des propriétés individuelles de mise en attente :  
  
-   **MaxThreshold**: les limites supérieures, en secondes, de l’heure à laquelle une orchestration peut être bloquée au niveau d’un abonnement avant d’être mise en attente.  
  
-   **MinThreshold**: la limite inférieure, en secondes, de l’heure à laquelle une orchestration peut être bloquée au niveau d’un abonnement avant d’être mise en attente.  
  
-   **ConstantThreshold**: seuil dynamique qui fluctue généralement entre les valeurs minimales et maximales spécifiées. Vous pouvez toutefois définir un seuil fixe en affectant une valeur à cette propriété. La valeur -1 indique au moteur de ne pas utiliser un seuil constant. N'affectez pas à cette propriété une valeur autre que -1 car cela désactiverait la limitation basée sur la mise en attente.  
  
## <a name="virtualmemorythrottlingcriteria"></a>VirtualMemoryThrottlingCriteria  
 Actuellement, la mémoire virtuelle peut générer un goulot d'étranglement sur les machines 32 bits en raison de l'absence de gestion de la fragmentation des segments de mémoire, et vous devez donc définir également une limitation sur cette ressource. Modifiez la configuration si la valeur /3Go est définie ou si les hôtes sont exécutés sur une plateforme 64 bits. Les valeurs d'utilisation optimale et maximale sont exprimées en Mo.  
  
 Voici les descriptions des propriétés individuelles pour VirtualMemoryThrottlingCriteria :  
  
-   **OptimalUsage**: quantité d’utilisation de mémoire virtuelle à partir de quels mise en attente de limitation commence entrent en vigueur. À ce stade, **TestThreshold** a la valeur **MaxThreshold** et toute utilisation de mémoire supérieure à **OptimalUsage** entraîne **TestThreshold**soit inférieure à **MaxThreshold**.  
  
-   **MaximalUsage**: quantité d’utilisation de mémoire virtuelle qui mise en attente de limitation est au maximum. À ce stade, **TestThreshold** a la valeur **MinThreshold** et toute utilisation de mémoire inférieure à **MaximalUsage** entraîne **TestThreshold** est supérieure à **MinThreshold**.  
  
-   **IsActive**: une valeur booléenne indiquant si la limitation de mémoire virtuelle est active.  
  
## <a name="privatememorythrottlingcriteria"></a>PrivateMemoryThrottlingCriteria  
 Cette propriété est un critère de limitation utile mais les valeurs appropriées dépendent de l'exécution éventuelle d'autres services Windows sur l'ordinateur. Si l'ordinateur dispose de beaucoup de mémoire et n'est pas partagé avec autres services Windows, vous pouvez augmenter ces valeurs de manière significative.  
  
 Voici les descriptions des propriétés individuelles pour PrivateMemoryThrottlingCriteria :  
  
-   **OptimalUsage**: quantité d’utilisation de mémoire privée, en Mo, le mise en attente de limitation commence à prendre effet. À ce stade **TestThreshold** a la valeur **MaxThreshold** et toute utilisation de mémoire supérieure à **OptimalUsage** entraîne **TestThreshold**soit inférieure à **MaxThreshold**.  
  
-   **MaximalUsage**: quantité d’utilisation de mémoire privée, en Mo, le mise en attente de limitation est au maximum. À ce stade **TestThreshold** a la valeur **MinThreshold** et toute utilisation de mémoire inférieure à **MaximalUsage** entraîne **TestThreshold** est supérieure à **MinThreshold**.  
  
-   **IsActive**: une valeur booléenne indiquant si la limitation de la mémoire privée est active.  
  
## <a name="physicalmemorythrottlingcriteria"></a>PhysicalMemoryThrottlingCriteria  
 Il existe également une limitation de la mémoire physique où les valeurs sont exprimées en pourcentage de la mémoire utilisée et non en Mo. Cette propriété est désactivée par défaut mais vous pouvez la définir si besoin est.  
  
 Voici les descriptions des propriétés individuelles pour PhysicalMemoryThrottlingCriteria :  
  
-   **OptimalUsage**: pourcentage optimal de la mémoire physique à utiliser pour les instances d’hôte.  
  
-   **MaximalUsage**: le pourcentage maximal de mémoire physique à utiliser pour les instances d’hôte.  
  
-   **IsActive**: valeur booléenne indiquant si la limitation de la mémoire physique est active.  
  
## <a name="dehydration-properties-behavior"></a>Comportement des propriétés de mise en attente  
 BizTalk Server utilise les propriétés de mise en attente pour décider du moment où il convient de mettre en attente ou de réalimenter les orchestrations. Dans des conditions de charge normales, les valeurs de mise en attente par défaut sont suffisantes, mais si le système fonctionne avec de lourdes charges et que vous souhaitiez modifier les caractéristiques de performances, vous devrez procéder à un réglage manuel.  
  
 Le comportement de mise en attente de BizTalk Server dépend entièrement de la quantité de mémoire disponible et de la quantité de mémoire utilisée. Il varie en fonction des quantités de mémoire et est différent sur les hôtes 32 bits et les hôtes 64 bits.  
  
 Les propriétés de mise en attente font la distinction entre octets privés et octets virtuels pour l'hôte de l'orchestration :  
  
-   **Octets virtuels**. Il s’agit de taille actuels, en octets, de l’espace d’adressage virtuel à l’aide de la procédure. L'utilisation de l'espace d'adressage virtuel n'implique pas nécessairement une utilisation correspondante des pages soit du disque, soit de la mémoire centrale. L'espace virtuel reste limité, et le processus peut restreindre sa capacité à charger des bibliothèques.  
  
-   **Octets privés**. Taille actuelle, en octets, de la mémoire allouée par le processus et qui ne peut pas être partagé avec d'autres processus.
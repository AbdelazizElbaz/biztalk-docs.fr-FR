---
title: "Une exception de sécurité s’est produite durant la réflexion d’un assembly BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca28c534b910479be3ae6ad26bd1e0a27a1637d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-security-exception-occurred-while-reflecting-a-biztalk-assembly"></a>Exception de sécurité lors de la mise en correspondance de l'assembly BizTalk
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Exception de sécurité lors de la mise en correspondance de l'assembly BizTalk « {0} ». Ce problème peut survenir lorsque l'assembly est situé dans un dossier réseau partagé. Pour corriger ce problème, essayez l’une des opérations suivantes : 1. Copiez l'assembly et ses dépendances sur l'ordinateur local. 2. Ajustez la stratégie de sécurité de l'exécution de la configuration .NET afin d'autoriser l'accès.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lorsque vous tentez de publier un assembly BizTalk situé sur un partage réseau sans la stratégie .NET appropriée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Outre la procédure décrite dans le message d'erreur, copiez l'assembly localement. Vous pouvez également modifier la stratégie pour accorder une confiance totale à l'intranet local.  
  
 **À l’aide de l’outil Code Access Security Policy (Caspol.exe)**  
  
 Vous pouvez approuver un dossier de votre ordinateur local au niveau Utilisateur avec des autorisations d'utilisateur normales. Pour approuver un emplacement réseau, vous devez disposer de privilèges d'administrateur et modifier la stratégie de sécurité au niveau Ordinateur. Ce niveau est indépendant du niveau de stratégie Utilisateur. Il n'accorde pas de confiance totale à la zone Intranet, contrairement à la stratégie Utilisateur. Les niveaux de stratégie doivent être cohérents.  
  
 **Pour accorder une confiance totale à un dossier local**  
  
-   Tapez la commande suivante dans l'invite de commandes Visual Studio :  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 **Pour accorder une confiance totale à un dossier réseau**  
  
-   Tapez la commande suivante dans l'invite de commandes Visual Studio :  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```
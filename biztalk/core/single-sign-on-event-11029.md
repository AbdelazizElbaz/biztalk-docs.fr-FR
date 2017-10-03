---
title: "Single Sign-On : Événement 11029 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd7cb5b0-532c-4f50-849d-4d1644026463
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5f24cee6fcbe7db5ce0b4f31d458a5a29118c3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11029"></a>Single Sign-On : Événement 11029
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11029|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_CASE_SENSITIVE|  
|Texte du message|La base de données SSO respecte la casse. Le serveur SSO s'exécutera en respectant la casse. Pour plus d'informations, reportez-vous à la documentation.%r|  
  
## <a name="explanation"></a>Explication  
 Par défaut, le serveur SSO ne respecte pas la casse. Toutefois, la base de données SSO du serveur SQL Server a été configurée de façon à respecter la casse. Par conséquent, le serveur SSO respectera également la casse.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Ayez cela à l'esprit lorsque vous spécifiez des noms d'applications ainsi que des noms de comptes externes, car ils respectent désormais la casse. Pour plus d’informations, consultez [serveur SSO](../core/sso-server.md).
---
title: "Single Sign-On : Événement 11054 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59dc801d-fc78-4561-8a26-9d815c86d842
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c4d71bc77f36231ddec939faf5e904e45017614
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11054"></a>Single Sign-On : Événement 11054
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11054|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_APP_USERS_NOT_GROUP|  
|Texte du message|Le compte Utilisateurs d'applications contient un ou plusieurs comptes individuels (différents des comptes de groupe). Si ces comptes individuels sont supprimés dans Active Directory ou sur l'ordinateur local, ils doivent être retirés rapidement du système SSO, sinon ils présentent un risque pour la sécurité.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Utilisateurs de l’application : %2 %r<br /><br /> Les comptes individuels : %3|  
  
## <a name="explanation"></a>Explication  
 La suppression d'un compte individuel dans Active Directory ou sur l'ordinateur local ne le supprime pas automatiquement du système SSO. Cela signifie que si le compte UTILISATEUR1 était supprimé localement, puis qu'un autre utilisateur (par exemple, un nouvel employé) se connectait au système en utilisant ce nom, le système SSO accorderait au nouvel UTILISATEUR1 tous les droits de sécurité détenus par l'UTILISATEUR1 d'origine. Cela pose un problème de sécurité.  
  
 Il est recommandé que les comptes d'administration SSO utilisent des comptes de groupe Active Directory (et non des comptes individuels).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action n'est nécessaire tant qu'un compte individuel n'est pas supprimé dans Active Directory ou sur l'ordinateur local. Vous devez alors supprimer le compte individuel sur le système SSO dès que possible.
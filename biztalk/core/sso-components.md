---
title: Composants SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, synchronizing [SSO]
- SSO, components
- SSO, password synchronization
- SSO, sub-services
ms.assetid: e29e68df-f770-4220-a9f8-cb9323403017
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1111f1a0dfac47412ae28b58f93ddc51e1f562b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-components"></a>Composants de l’authentification unique
Les sous-services du service d'authentification unique de l'entreprise sont les suivants :  
  
-   **Mappage.** ce composant mappe le compte d'utilisateur du système Windows aux comptes d'utilisateur des systèmes principaux.  
  
-   **Liste de choix.** ce composant recherche les informations d'identification dans la base de données SSO du système principal. Il s'agit du composant d'exécution SSO.  
  
-   **Administration.** ce composant gère les applications associées et les mappages correspondants.  
  
-   **Clé secrète.** ce composant génère le secret principal et le distribue aux autres serveurs SSO du système. Il n'est actif que sur le serveur SSO qui agit comme le serveur de secret principal.  
  
-   **Synchronisation de mot de passe.** ce composant simplifie l'administration de la base de données SSO et synchronise les mots de passe au sein des annuaires d'utilisateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur d’authentification unique](../core/sso-server.md)   
 [L’installation de l’authentification unique](../core/installing-sso.md)
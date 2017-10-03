---
title: "Interface de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e3c2d3-a7e9-4a45-965d-bfe4bf200c34
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee479a29a424228b31bc3fcd5752f8da7cc3ce28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-interface"></a>Interface de l’authentification unique

## <a name="interfaces"></a>Interfaces
Le tableau suivant décrit les interfaces COM et .NET Framework qui composent l'interface de l'authentification unique.  
  
|.NET|COM| Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOAdmin|Interface ISSOAdmin (COM)|Crée, met à jour et supprime une application SSO. Réalise également d'autres fonctions d'administration.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOConfigStore|Interface ISSOConfigStore (COM)|Obtient et définit des informations dans le magasin de configuration de l’authentification unique.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup1|Interface ISSOLookup1 (COM)|Permet de consulter les informations d’identification externes de l’utilisateur actuel pour une application spécifiée.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOLookup2|Interface ISSOLookup2 (COM)|Comme ci-dessus, mais permet également de consulter les informations d'identification Windows d'un utilisateur externe spécifié.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapper|Interface ISSOMapper (COM)|Permet de définir les informations d'identification externes de l'utilisateur actuel pour une application spécifiée.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOMapping|Interface ISSOMapping (COM)|Crée et gère le mappage entre les utilisateurs et les applications associées.|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOTicket|Interface ISSOTicket (COM)|Crée le ticket contenant les informations de sécurité appropriées. Ce ticket est ensuite envoyé avec le message approprié de votre application.|  


## <a name="password-sync-helper"></a>Programme d'aide à la synchronisation des mots de passe  
 En outre, Host Integration Server prend en charge le composant Programme d’aide à la synchronisation des mots de passe. Vous pouvez l’utiliser lors de la conception des composants de synchronisation des mots de passe. Le tableau suivant décrit les interfaces COM et .NET Framework présentées par le Programme d’aide à la synchronisation des mots de passe.  
  
|.NET|COM| Description|  
|----------|---------|-----------------|  
|Microsoft.EnterpriseSingleSignOn.Interop.ISSOPSWrapper|Interface ISSONotification (COM)|Gère les changements de mot de passe vers et depuis des systèmes d’exploitation non-Windows.|  
||Structure SExternalAccount (COM)|Décrit un compte externe.|  
||Structure SPasswordChange (COM)|Décrit un changement de mot de passe.|  
||Structure SPasswordChangeComplete (COM)|Décrit la fin d’un changement de mot de passe.|  
||Structure SStatus (COM)|Décrit une erreur ou un événement.|  
||Structure SAdapterInGroup (COM)|Décrit les adaptateurs d’un groupe donné.|  
||Structure SAdapter (COM)|Décrit un adaptateur spécifique.|

## <a name="see-also"></a>Voir aussi
Afficher les objets COM de l’authentification unique [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
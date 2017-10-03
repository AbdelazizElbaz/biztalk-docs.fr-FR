---
title: Comment configurer un adaptateur de synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0effdc9b-4aee-4674-90c5-03dfd7cc4cd6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f0be0146e905ef291942bd30adc111eff89e989
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-password-sync-adapter"></a>Comment configurer un adaptateur de synchronisation de mot de passe
Après avoir créé votre adaptateur de synchronisation de mot de passe, vous devez le charger sur un système. En outre, vous devez informer les systèmes d’authentification unique de l’entreprise (ENTSSO) et de stockage des informations de configuration que votre application correspond à un adaptateur de synchronisation de mot de passe. Vous devez enregistrer le magasin de configuration pour des raisons de sécurité : votre adaptateur demandera de mises à jour les mots de passe et autres informations d’identification. Par conséquent, l'authentification unique de l'entreprise (ENTSSO) doit être informée de l’autorisation d'un adaptateur donné à demander de telles autorisations.  
  
### <a name="to-configure-a-password-sync-adapter"></a>Pour configurer un adaptateur de synchronisation de mot de passe  
  
1.  Créez votre adaptateur avec le magasin de configuration à l'aide de l'outil ssops.  
  
     Avec ssops, vous pouvez charger un fichier de configuration XML dans la base de données de configuration qui décrit votre application au système d’authentification unique de l’entreprise.  
  
2.  Une fois que vous avez créé l’adaptateur avec la base de données de configuration, vous pouvez modifier les informations de l’adaptateur avec `ISSOPSAdmin.SetAdapterProperties`.  
  
     Les deux méthodes sont semblables, si ce n’est que `SetAdapterProperties` envoie un message à l’adaptateur lorsque les informations de configuration sont modifiées.  
  
3.  Pour supprimer un adaptateur, utilisez ISSOAdmin.DeleteApplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation des mots de passe](../core/synchronizing-passwords.md)
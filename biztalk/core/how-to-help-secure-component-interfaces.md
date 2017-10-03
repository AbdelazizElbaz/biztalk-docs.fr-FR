---
title: "Interfaces de façon sécurisée de composant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, helping to secure
- security, component interfaces
ms.assetid: 03b2af44-78e7-4fdc-bfa3-7697b2a60986
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54136aaeae9578ae4e438c5bd8b95b902d618f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-help-secure-component-interfaces"></a>Sécurisation des interfaces de composant
Avant de pouvoir commencer à tester une interface de composant, vous devez en configurer la sécurité. La procédure suivante décrit comment configurer la sécurité d’interface de composant pour PeopleSoft Version 8.4, mais vous pouvez utiliser la procédure pour la Version 8.1.  
  
### <a name="to-configure-interface-security"></a>Pour configurer la sécurité de l'interface  
  
1.  Développez **PeopleTools**, développez **sécurité**, développez **profils utilisateur**, puis développez **autorisations et rôles**.  
  
     ![](../core/media/psadapter-47-ps-configsecurity1.gif "PSAdapter_47_PS_ConfigSecurity1")  
  
2.  Cliquez sur **listes d’autorisations**.  
  
3.  Cliquez sur **Rechercher**.  
  
     ![](../core/media/psadapter-48-ps-configsecurity2.gif "PSAdapter_48_PS_ConfigSecurity2")  
  
4.  Dans le **recherche des listes des autorisations** volet, sélectionnez la liste des autorisations appropriées.  
  
     La fenêtre suivante s'affiche.  
  
     ![](../core/media/psadapter-49-ps-configsecurity3.gif "PSAdapter_49_PS_ConfigSecurity3")  
  
5.  Cliquez sur la flèche droite en regard du **heures de connexion** onglet pour afficher plus d’onglets.  
  
     ![](../core/media/psadapter-50-ps-configsecurity4.gif "PSAdapter_50_PS_ConfigSecurity4")  
  
6.  Cliquez sur le **Interfaces de composant** onglet.  
  
7.  Cliquez sur le + (signe) pour ajouter une nouvelle ligne à la **Interfaces de composant** liste.  
  
     Dans le champ qui s'affiche, vous pouvez taper le nom de l'interface de composant.  
  
     ![](../core/media/psadapter-51-ps-configsecurity5.gif "PSAdapter_51_PS_ConfigSecurity5")  
  
8.  Tapez le nom d’interface de composant, puis cliquez sur **modifier**.  
  
     Cet exemple utilise l'interface de composant AR_ITEM_AGENT.  
  
     ![](../core/media/psadapter-52-ps-configsecurity6.gif "PSAdapter_52_PS_ConfigSecurity6")  
  
9. Dans la liste, sélectionnez le niveau d’accès souhaité pour chaque méthode, puis cliquez sur **OK**.  
  
     La fenêtre suivante s'affiche.  
  
     ![](../core/media/psadapter-53-ps-configsecurity7.gif "PSAdapter_53_PS_ConfigSecurity7")  
  
10. Faites défiler vers le bas dans le volet droit, puis cliquez sur **enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)   
 [Annexe c : à l’aide des Interfaces de composant](../core/appendix-c-using-component-interfaces.md)
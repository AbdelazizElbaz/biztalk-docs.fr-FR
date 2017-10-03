---
title: "Page Paramètres d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67f10b8b-9a32-40ca-9ce4-0b69e159c36c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5ce03e5284122e8c1de9bd4e5c2d69c392174e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fault-settings-page"></a>Page Paramètres des erreurs
Figure 1 montre la page Paramètres de l’erreur. Cette page affiche une plage de paramètres d’administration que vous pouvez modifier.  
  
 ![Page Paramètres d’erreur](../esb-toolkit/media/ch8-faultsettingspage.gif "Ch8-FaultSettingsPage")  
  
 **Figure 1**  
  
 **La page Paramètres de pannes du portail de gestion ESB**  
  
 La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page Paramètres de pannes du portail de gestion ESB :  
  
-   Pour modifier les options d’audit, sélectionnez les cases à cocher pour chaque événement que vous souhaitez auditer. Les événements disponibles sont l’enregistrement des paramètres modifiés, renvoyés réussie d’une erreur après avoir modifié et Échec lors de la soumettre à nouveau une erreur.  
  
-   Le portail gère une file d’attente des alertes générées par le service d’alerte. Vous pouvez modifier les paramètres pour ce service dans le **Options d’alerte pour file d’attente** section de la page. Vous pouvez activer ou désactiver le service, spécifiez son interaction avec le service d’annuaire Microsoft Active Directory et contrôler la taille de lot de file d’attente et l’intervalle d’interrogation.  
  
-   Pour modifier les paramètres pour le service d’alertes par courrier électronique, utilisez les contrôles dans le **Options d’alerte par courrier électronique** section de la page. Vous pouvez activer ou désactiver le service ; Spécifiez le serveur de messagerie et l’adresse « de » ; modifier la taille d’interrogation intervalle et le traitement par lots ; et spécifiez le chemin d’accès aux fichiers XSLT utilisé par le service.  
  
> [!NOTE]
>  Lorsque vous installez et configurez le portail ESB et le service d’alerte de portail, vous devez entrer les valeurs dans cette page. Pour plus d’informations, consultez [l’installation du portail de gestion ESB](http://go.microsoft.com/fwlink/?LinkId=188554).
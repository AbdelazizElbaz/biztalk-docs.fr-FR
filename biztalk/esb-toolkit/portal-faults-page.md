---
title: "Portail de défauts de Page | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b11e3492-da1a-43f3-acf8-3775b5cbc2c5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 294ba24516cccbf6c15ada26d28f169a6eb45c98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="portal-faults-page"></a>Portail de défauts de Page
Figure 1 montre la page d’erreurs. Cette page affiche les propriétés principales de chaque erreur, et il permet de trier et filtrer des fonctionnalités qui prennent en charge l’analyse détaillée des erreurs sur une plage de critères, tels que le type d’erreur et d’heure. Un lien pour chaque erreur vous permet d’afficher plus de détails dans l’Afficheur des messages d’erreur.  
  
 ![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")  
  
 **Figure 1**  
  
 **La page d’erreurs du portail de gestion ESB**  
  
 La liste suivante explique comment vous pouvez utiliser les fonctionnalités de la page d’erreurs de portail de gestion ESB :  
  
-   Pour filtrer la liste d’erreurs affichées dans la page, utilisez les listes déroulantes et les zones de texte au-dessus de la liste d’erreurs. Vous pouvez filtrer les lignes affichées comme suit :  
  
    -   Sélectionnez l’une des applications BizTalk installées dans le **Application** liste déroulante.  
  
    -   Spécifiez la période au cours de laquelle l’erreur s’est produite en sélectionnant **heure, jour, semaine, mois, trimestre, année,** ou **tous les** dans les **récupérer les enregistrements au sein de la dernière** liste déroulante.  
  
    -   Spécifiez le nombre de lignes à afficher dans la page dans le **enregistrements par Page** liste déroulante.  
  
    -   Tapez un numéro de code d’erreur dans le **Code d’erreur** zone de texte.  
  
    -   Tapez tout ou partie du nom de catégorie d’erreur dans le **catégorie** zone de texte.  
  
    -   Tapez tout ou partie du texte de type erreur dans le **Type d’erreur** zone de texte.  
  
    -   Tapez une valeur pour le niveau de gravité erreur minimum et/ou maximum (tel que **avertissement, erreur, grave,** ou **critique**) dans le **gravité d’erreur Min** et **Max Fault Gravité** zones de texte.  
  
-   Après avoir spécifié les valeurs pour un ou plusieurs de ces contrôles, cliquez sur le **appliquer des filtres** bouton Appliquer tous les critères spécifiés.  
  
-   Cliquez sur un en-tête de colonne pour afficher les lignes de message d’erreur dans l’ordre de ce contenu de la colonne, puis cliquez sur Nouveau pour afficher la liste dans l’ordre inverse.  
  
-   Pour afficher plus de détails d’une erreur dans la liste, ou pour modifier et renvoyez le message qu’il contient, cliquez n’importe où dans la ligne pour cette erreur pour l’ouvrir dans le [Afficheur des messages d’erreur Portal](../esb-toolkit/portal-fault-message-viewer.md).
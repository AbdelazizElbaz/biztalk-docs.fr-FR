---
title: Pour créer une Configuration de processus à l’aide de la spécification PIP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs, PIP settings
- PIPs, PIP secifications
- process configuration, PIPs
- PIPs, process configuration
ms.assetid: 64f0f5fb-f880-4ef1-95d7-2575b8d0bcff
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777f32e5a9e035f6009f5450eb48ae8286159f05
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="using-the-pip-specification-to-create-a-process-configuration"></a>Pour créer une Configuration de processus à l’aide de la spécification PIP
Après avoir téléchargé un processus PIP (Partner Interface) de l’organisation RosettaNet (RosettaNet.org), le package de téléchargement inclut un document de spécification PIP. Ce document contient des conseils sur les paramètres à utiliser lorsque vous créez une configuration de processus dans le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Console de gestion.  
  
## <a name="how-pip-settings-map-to-the-pip-specification"></a>Comment PIP mappage de paramètres à la spécification PIP  
 Le tableau suivant décrit comment les paramètres de PIP mappent aux informations contenues dans la spécification PIP RosettaNet.  
  
|Paramètre de Configuration de processus|Pour plus d’informations dans la spécification PIP|  
|-----------------------------------|------------------------------------------|  
|Code de processus|Sous-titre dans la page de titre, par exemple, « PIP3A4 »|  
|Version|Sous-titre d’identificateur de Version PIP sur la page de titre, par exemple, « 02.02.00 »|  
|Nom du processus|Sous-titre dans la page de titre, par exemple, « demande de bon de commande »|  
|Description (onglet Général)|Section 3.1, définition de processus d’entreprise|  
|Non-répudiation requise|Contrôles de table 3-3 : entreprise activité performances|  
|Temps pour accuser réception (secondes)|Contrôles de table 3-3 : entreprise activité performances|  
|Une autorisation est requise ?|Contrôles de table 3-3 : entreprise activité performances|  
|Confidentialité persistante requise|(Aucune référence à partir de la spécification PIP)|  
|Est un Transport sécurisé requis ?|Tableau 4-3 : Message Exchange contrôles|  
|Action unique|Section 4.3, spécification de la boîte de dialogue Business Transaction|  
|Non-répudiation de l'origine et du contenu|Contrôles de table 3-3 : entreprise activité performances|  
|Nombre de tentatives|Contrôles de table 3-3 : entreprise activité performances|  
|Durée d'exécution|Contrôles de table 3-3 : entreprise activité performances|  
|Nom|Activité d’entreprise table 3-3 : contrôles performances (nom de l’activité)|  
|Type|(Aucune référence à partir de la spécification PIP - pour une utilisation ultérieure)|  
|Description (onglets initiateur et de réponse)|Tableau 3-4 : PIP des Documents d’entreprise|  
|Nom (onglets initiateur et de réponse)|Tableau 3-4 : PIP des Documents d’entreprise|  
|Rôle (onglets initiateur et de réponse)|Tableau 3-1 : les Descriptions de rôle de partenaire|  
|Description du rôle (onglets initiateur et de réponse)|Tableau 3-1 : les Descriptions de rôle de partenaire|  
|Type de rôle (onglets initiateur et de réponse)|Tableau 3-1 : les Descriptions de rôle de partenaire|  
|Service|Spécification de composant de réseau de tableau 4-1 :|  
|Classification du service.|Spécification de composant de réseau de tableau 4-1 :|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour créer ou modifier une configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)
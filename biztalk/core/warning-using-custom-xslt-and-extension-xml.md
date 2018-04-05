---
title: 'Avertissement : utilisation de XML avec extensions et XSLT personnalisé | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.usingCustomXsltAndExtensionXML
ms.assetid: b86da5fb-6435-4e3b-89b6-d9d036b5152b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90644aec738345e3a36286cc62aaa7a355e04348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="warning---using-custom-xslt-and-extension-xml"></a>Avertissement : utilisation de XML avec extensions et XSLT personnalisés
**Code d’erreur**  
  
 btm1035  
  
 **Explication**  
  
 Les valeurs de remplacement pour le **chemin du XSLT personnalisé** et **XML avec extensions personnalisées** contrôle les messages d’instance de sortie générés par ce mappage, en ignorant les mappages de propriétés spécifié entre les schémas source et de destination. Si cela est intentionnel, ne tenez pas compte de cet avertissement.  
  
 Un scénario dans lequel il est valide consiste à utiliser le Mappeur BizTalk pour générer un XSLT préliminaire pour le mappage, modifiez ce XSLT manuellement pour répondre aux exigences supplémentaires spécifiques, puis spécifiez le fichier modifié en tant que la valeur de la **cheminduXSLTpersonnalisé** propriété, remplaçant ainsi le XSLT préliminaire lors des opérations de mappage ultérieures.  
  
 **Action de l’utilisateur**  
  
 Si vous ne souhaitez pas remplacer le mappage spécifié dans ce mappage, supprimez les valeurs de remplacement pour le **chemin du XSLT personnalisé** propriété et la **XML avec extensions personnalisées** propriété, comme il convient.
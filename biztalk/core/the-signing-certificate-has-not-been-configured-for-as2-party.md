---
title: "Le certificat de signature n’a pas été configuré pour le tiers AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82928a39-3acf-447b-a0e8-f7c25b6f38dc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61802b5e86319d0fe73f11c22249b72af1441b5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-signing-certificate-has-not-been-configured-for-as2-party"></a>Le certificat de signature n'a pas été configurée pour le tiers AS2
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur AS2|  
|Nom symbolique|SigningCertNotConfiguredError|  
|Texte du message|Le certificat de signature n'a pas été configuré pour le tiers AS2.  AS2-à partir de : {0} AS2-pour : {1}|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant car le certificat de signature n'était pas configuré pour le groupe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, configurez le certificat de signature en effectuant l'une des opérations suivantes :  
  
1.  Ouvrez la console Administration de BizTalk Server.  
  
2.  Accédez au nœud Groupe, puis cliquez sur le nœud Certificat.  
  
3.  Entrez le nom commun et l'empreinte du certificat.
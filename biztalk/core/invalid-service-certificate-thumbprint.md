---
title: "Empreinte numérique du certificat de service non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22e7d74e-40ec-4187-9246-bc8da2a9ce86
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a465d631e72bc27c6b24274deb31e396037aa182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-service-certificate-thumbprint"></a>Empreinte de certificat de service non valide
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Empreinte de certificat de service non valide ; elle doit comporter 40 chiffres hexadécimaux|  
  
## <a name="explanation"></a>Explication  
 Une empreinte de certificat de service non valide a été spécifiée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Dans le code de configuration du port WCF, la propriété Certificat de service de l'interface utilisateur attend 40 chiffres hexadécimaux. Exemple : 798A68E7A3E6F2CCC6929FC4AF2A15A9EED66E39  
  
 Pour plus d'informations sur les certificats, consultez la ressource suivante :  
  
-   [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)
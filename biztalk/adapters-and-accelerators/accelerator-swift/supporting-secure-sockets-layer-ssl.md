---
title: "Prise en charge sécurisée des Sockets Layer (SSL) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SSL
ms.assetid: 012a5be0-bab8-4a60-9d63-b9684b91e4a7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086ec1715d76a25649cb2285b31b3df790b0fe3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="supporting-secure-sockets-layer-ssl"></a>Prise en charge de Secure Sockets Layer (SSL)
Pour implémenter le protocole Secure Sockets Layer (SSL) dans votre déploiement entre les ordinateurs clients et les serveurs MRSR, vous devez demander et configurer un certificat de le « Authentification serveur » sur vos serveurs Internet Information Services (IIS).  
  
 Un certificat doit être utilisé pour tous les serveurs de votre cluster d’équilibrage de charge réseau (NLB). Vous devez vous assurer que le nom utilisé dans la demande de certificat est le nom d’hôte virtuel au lieu d’un nom de serveur individuels.
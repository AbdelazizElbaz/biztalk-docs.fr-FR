---
title: "Interfaces d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7398aeb-7c1c-400e-a552-d0ab39e55a0b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717adcf5d4a706a7cc072b42b224ab0f9f8cc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-interfaces"></a>Interfaces d’adaptateur
Les adaptateurs personnalisés doivent implémenter trois interfaces. Il existe en outre deux interfaces facultatives.  
  
## <a name="mandatory-interfaces"></a>Interfaces obligatoires  
 Tous les adaptateurs doivent implémenter les interfaces suivantes.  
  
### <a name="ibasecomponent"></a>IBaseComponent  
 Cette interface détaille le **nom**, **Version**, et **Description** de l’adaptateur.  
  
### <a name="ibttransport"></a>IBTTransport  
 Cette interface détaille le **Type de Transport** et **ClassID** de la carte.  
  
### <a name="ibtbatchcallback"></a>IBTBatchCallback  
 Cette interface est une interface de rappel par l'intermédiaire de laquelle l'adaptateur reçoit les informations d'état et d'erreur liées à un lot de messages soumis au moteur de messagerie.  
  
## <a name="optional-interfaces"></a>Interfaces facultatives  
 Les adaptateurs peuvent implémenter les interfaces ci-dessous, si besoin est.  
  
### <a name="ipersistpropertybag"></a>IPersistPropertyBag  
 Il s'agit d'une interface de configuration par le biais de laquelle la configuration du gestionnaire est fournie à l'adaptateur. Cette interface est requise uniquement pour les adaptateurs disposant d'informations de configuration de gestionnaire.  
  
### <a name="ibttransportcontrol"></a>IBTTransportControl  
 Cette interface permet d'initialiser et d'arrêter un adaptateur. Le proxy de transport de l'adaptateur lui est transmis par l'intermédiaire de cette interface. Cette interface n'est pas requise pour les adaptateurs isolés.
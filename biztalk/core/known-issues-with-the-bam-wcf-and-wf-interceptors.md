---
title: "Problèmes connus avec l’analyse BAM intercepteurs WCF et WF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2407809-1f71-41a9-b305-722a7f86af5b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42078eb2b1272072016ded9a117e88ddf4fda038
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-bam-wcf-and-wf-interceptors"></a>Problèmes connus avec les intercepteurs WCF et WF BAM
Cette section fournit des informations sur certains problèmes connus que vous pouvez rencontrer lors de l'utilisation des intercepteurs BAM pour Windows Workflow Foundation ou Windows Communication Foundation.  
  
## <a name="intercepting-a-dynamically-generated-wcf-assembly-hosted-in-iis"></a>Interception d'un assembly WCF généré de manière dynamique et hébergé dans IIS  
 Lorsque vous faites appel à IIS pour héberger une application Windows Communication Foundation intégrée (par exemple, un fichier de service qui spécifie la source de l'assembly), l'assembly WCF est généré de manière dynamique, il reçoit un nom de fichier arbitraire et il est placé dans le dossier temporaire asp.net. Le fichier de configuration de l'intercepteur exige les informations sur le manifeste : étant donné que les caractères génériques ou d'autres méthodes dynamiques permettant de spécifier le manifeste ne sont pas disponibles pour les fichiers de configuration de l'intercepteur, vous devez recompiler votre service, puis créer le fichier de configuration de l'intercepteur ou redéployer celui existant après avoir déployé toutes les pages Web asp.net contenant du code WCF incorporé.  
  
## <a name="use-of-the-bam-interceptor-for-windows-workflow-foundation-is-not-supported-in-office-and-sharepoint-server"></a>L'utilisation de l'intercepteur BAM pour Windows Workflow Foundation n'est pas prise en charge dans Office ni Sharepoint Server  
 Office et Windows Sharepoint Server ne lisent pas à partir du fichier de configuration de l'application lors de l'initialisation du composant d'exécution WF. Par conséquent, l'intercepteur BAM pour WF peut être configuré pour une application, mais il ne sera pas chargé dans le composant d'exécution du workflow lorsqu'il est hébergé dans ces environnements.  
  
## <a name="client-service-locks-when-intiating-a-distributed-transaction"></a>Le service client est verrouillé lors de l'initialisation d'une transaction distribuée  
 Si l'opération de service ne participe pas à la transaction initiée par le client et que ce dernier appelle le service d'après le contexte d'une étendue de transaction, un blocage peut survenir, notamment lorsque des données sont collectées au niveau du client avant la demande d'envoi et au niveau du service par la demande de réception pour la même activité.  
  
 Pour éviter cette situation, vous devez indiquer que le client ne participe pas à la transaction en déclarant « Enlist = false » dans l'attribut `ConnectionString` du client pour l'extension de comportement BAM dans le fichier app.config du client, comme décrit ci-dessous.  
  
```  
<behavior name="bamClientBehavior">  
  <bamClientBehaviorExtension ConnectionString="Integrated Security=SSPI;Initial Catalog=BAMPrimaryImport;Data Source=.;  Enlist=false"  PollingIntervalSec="1500" />  
</behavior>  
```  
  
## <a name="open-wcf-channel-before-sending-a-message-when-bam-interceptors-are-used"></a>Ouverture du canal WCF avant l'envoi d'un message lors de l'utilisation des intercepteurs BAM  
 Lorsque l'intercepteur BAM est activé pour WCF avec une liaison BasicHttp, le proxy doit appeler proxy.Open() pour ouvrir de manière explicite le canal. Si cette condition n'est pas remplie, l'interception BAM risque d'échouer en générant une exception.
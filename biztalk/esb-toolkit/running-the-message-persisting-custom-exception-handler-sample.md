---
title: "Le Message de persistance d’exemple de gestionnaire d’exceptions personnalisé en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0a4c819-f6bd-4dea-8be9-e3006337665f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6d7927357e4c2be03ecd8b2e77d45558b5bc692
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-message-persisting-custom-exception-handler-sample"></a>Le Message de persistance d’exemple de gestionnaire d’exceptions personnalisé en cours d’exécution
L’exemple de gestionnaire d’exceptions personnalisé persistance Message montre un gestionnaire générique, faiblement couplé, qui reçoit des messages d’erreur, extrait les messages de Microsoft BizTalk qu’ils contiennent et les écrit en tant que fichiers de disque dans le système de fichiers.  
  
 L’exemple montre comment vous pouvez utiliser un gestionnaire d’exceptions personnalisé dans une orchestration. Lorsqu’un processus dans l’orchestration (EAIProcess.odx) rencontre une erreur, le Gestionnaire d’exceptions génère et publie un message d’erreur ESB. Ce message d’erreur inclut dans sa charge utile les messages (y compris leurs propriétés de contexte de BizTalk liées) qui ont été « en vol » lorsque l’exception s’est produite, ainsi que l’instance actuelle de System.Exception interceptée par le moteur d’Orchestration BizTalk. Lorsque cela se produit, un message « Refusé » et un message « Approved » sont conservées avec le message d’erreur.  
  
 Une deuxième orchestration nommée EAIGenericHandler.odx, qui est déployé dans une méthode découplée et agit comme un gestionnaire d’exceptions personnalisées, s’abonne au code d’erreur spécifique généré dans l’orchestration EAIGenericHandler.odx et consomme le message d’erreur. Ce gestionnaire d’exceptions extrait les messages d’origine (comme des documents de type sans) et les instances de System.Exception persistantes à l’origine dans le message d’erreur.  
  
 L’exemple de gestionnaire d’exceptions personnalisé persistance Message diffère de l’exemple de réparation et soumettez à nouveau gestionnaire d’exceptions personnalisé l’orchestration EAIGenericHandler.odx utilisée dans cet exemple ne dispose pas d’une dépendance sur les schémas utilisés dans la publication de l’erreur processus d’orchestration (EAIProcess.odx). Plus précisément, l’orchestration EAIGenericHandler.odx récupère les messages d’origine à partir du message d’erreur en tant qu’instances System.Xml.XmlDocument au lieu de messages typés selon les schémas utilisés dans l’orchestration EAIProcess.odx. Il renvoie également les messages sous forme de collection qui code peut énumérer facilement.  
  
 Le Gestionnaire d’exceptions personnalisé (EAIGenericHandler.odx) écrit ensuite le « Denied » et les messages « Approved » pour le fichier système emplacement \Source\Samples\Exception Handling\Test\Filedrop\EAIGenericHandler.PostTmpMsg.  
  
 En outre, il est un port d’envoi générique appelé tous. Exceptions_FILE configuré pour utiliser le pipeline GlobalFaultProcessor installé dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] infrastructure de gestion des exceptions. Ce port s’abonne à toutes les exceptions dans le système, les deux BizTalk Échec de routage des messages de message et les messages d’erreur ESB. L’infrastructure de gestion d’Exception les normalise toutes dans un format unique et sérialise à l’aide d’une instruction de traitement InfoPath de Microsoft à l’emplacement \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions.  
  
## <a name="installation"></a>Installation  
 Tous les exemples de gestion d’exception utilisent le même jeu de services principaux et les artefacts de l’application BizTalk. Par conséquent, vous devez installer les artefacts d’exemple de gestion d’exception qu’une seule fois pour être en mesure d’exécuter tous les l’exception des exemples de gestion. Pour plus d’informations sur la façon d’installer les exemples de gestion des exceptions, consultez [installant les exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md).  
  
## <a name="running-the-sample-application"></a>Exécution de l'exemple d'application  
 **Pour exécuter l’exemple de gestionnaire d’exceptions Message persistance personnalisée**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que la réception emplacement et envoyer une URL de port pointant vers les répertoires appropriés dans le dossier \Source\Samples\Exception Handling\Test\Filedrop. L’emplacement de réception doit spécifier le dossier EAIProcess.RequestPort, et l’URL de port d’envoi doit spécifier le dossier EAIGenericHandler.PostTmpMsg.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
3.  Démarrer l’exemple en copiant le fichier d’exemple nommé Request_EAIGenericHandler.xml, situé dans le dossier \Source\Samples\Exception Handling\Test\Data, dans le dossier spécifié pour l’emplacement de réception de la EAIProcess.RequestPort_FILE : \Source\Samples\ Exception Handling\Test\Filedrop\EAIProcess.RequestPort.  
  
4.  Ouvrez le dossier nommé EAIGenericHandler.PostTmpMsg (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop\). Vous verrez le message d’origine.  
  
## <a name="how-the-sample-works"></a>Fonctionne de l’exemple  
 Le message que vous envoyez Active l’orchestration EAIProcess. Lorsque l’orchestration EAIProcess traite le message, il tente de diviser 1 par le prix unitaire. Étant donné que le prix unitaire est égal à zéro, une exception de division par zéro se produit. Code du Gestionnaire d’événements de l’orchestration intercepte cette exception et crée un message d’erreur. La quantité commandée dans le message est inférieure à 10, la logique métier en décide que cette exception a un **FaultCode** champ à la valeur de **2000**.  
  
 L’orchestration EAIProcess publie le message d’erreur dans la boîte de Message BizTalk via un port à liaison directe, et l’orchestration se termine.  
  
 Une orchestration de gestionnaire d’erreur personnalisée nommée EAIGenericHandler, qui s’abonne aux messages avec un **FaultCode** champ à la valeur de **2000**, récupère le message d’erreur. Le code dans l’orchestration extrait tous les messages à partir du message d’exception (erreur) et les écrit dans les fichiers de disque.
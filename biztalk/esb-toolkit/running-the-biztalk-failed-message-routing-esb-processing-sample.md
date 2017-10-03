---
title: "Échec de l’exemple de traitement ESB du routage de Message en cours d’exécution BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2a536a0-cfc8-4ba3-adcd-2b8b580bff85
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a19f8c29c22638be97ae62dfea88d0d2feca6c55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-biztalk-failed-message-routing-esb-processing-sample"></a>Échec de l’exemple de traitement ESB du routage de Message BizTalk en cours d’exécution
L’exemple Microsoft BizTalk Échec de routage ESB de traitement du Message montre comment vous pouvez utiliser la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Exception Management Framework comme mécanisme d’universel à gérer, de sérialiser et de restituer des exceptions qui se produisent dans toutes les conditions dans [!INCLUDE[prague](../includes/prague-md.md)]. Cela inclut les exceptions générées par BizTalk Échec de routage des messages mécanisme et erreur messages générés par l’infrastructure de gestion d’Exception à partir d’une orchestration.  
  
 Le mécanisme de routage des messages a échoué BizTalk est la facilité de gestion des erreurs de [!INCLUDE[prague](../includes/prague-md.md)], à l’aide, le concepteur peut désigner la gestion automatique des échecs de messagerie comme alternative à traditionnel (maintenant) par défaut de la mise en échec messages dans la file d’attente « Suspendu ». Cette gestion automatique achemine un message d’erreur à n’importe quelle destination de routage abonnée, comme un port d’envoi ou d’une orchestration. Le message d’erreur est un clone du message d’origine avec toutes les propriétés précédemment promues rétrogradées et avec les propriétés sélectionnées associées à l’échec de la messagerie promue dans le contexte du message.  
  
 Pour activer le mécanisme de routage des messages a échoué BizTalk sur un port de réception ou un port d’envoi, sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, comme indiqué dans la Figure 1.  
  
 ![Routage activé](../esb-toolkit/media/ch6-enabledrouting.gif "§ 6-EnabledRouting")  
  
 **Figure 1**  
  
 **L’activation du mécanisme de routage des messages a échoué BizTalk**  
  
 Toutefois, il n'est pas un mécanisme similaire pour les erreurs ou les défaillances qui se produisent dans une orchestration. Au lieu de cela, le code dans le Gestionnaire d’exceptions d’une orchestration peut profiter de l’API de Framework Exception Management pour émuler la fonctionnalité de la méthode de routage des messages a échoué BizTalk.  
  
 Dans cet exemple, l’emplacement de réception nommé EAIProcess.RequestPort_FILE récupère les fichiers copiés à l’emplacement \Source\Samples\Exception Handling\Test\Filedrop\EAIProcess.RequestPort.  
  
 En outre, il est un port d’envoi générique appelé tous. Exceptions_FILE configuré pour utiliser le pipeline GlobalFaultProcessor installé dans le cadre de l’infrastructure de gestion d’Exception. Ce port s’abonne à toutes les exceptions qui se produisent dans le système, les deux BizTalk Échec de routage des messages de message et les messages d’erreur ESB, comme indiqué dans la Figure 2.  
  
 ![Port d’envoi](../esb-toolkit/media/ch6-sendport.gif "§ 6-ports d’envoi")  
  
 **Figure 2**  
  
 **Tous les. Abonnement de port pour tous les types d’exception ou d’échec d’envoi exceptions**  
  
 L’infrastructure de gestion d’Exception normalise toutes les exceptions dans un format unique et sérialise à l’aide d’une instruction de traitement InfoPath de Microsoft à l’emplacement \Source\Samples\Exception Handling\Test\Filedrop\All_Exceptions.  
  
## <a name="installation"></a>Installation  
 Tous les exemples de gestion d’exception utilisent le même jeu de services principaux et les artefacts de l’application BizTalk. Par conséquent, vous devez installer les artefacts d’exemple de gestion d’exception qu’une seule fois pour être en mesure d’exécuter tous les l’exception des exemples de gestion. Pour plus d’informations sur la façon d’installer les exemples de gestion des exceptions, consultez [installant les exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md).  
  
## <a name="running-the-sample-application"></a>Exécution de l'exemple d'application  
 **Pour exécuter l’exemple BizTalk Échec de routage ESB de traitement du Message**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que la réception emplacement et envoyer une URL de port pointant vers les répertoires appropriés dans le dossier \Source\Samples\Exception Handling\Test\Filedrop. L’emplacement de réception doit spécifier le dossier EAIProcess.RequestPort, et l’URL de port d’envoi doit spécifier le dossier All_Exceptions.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
3.  Copiez le fichier nommé FlatFileReceive_in.txt dans le dossier \Source\Samples\Exception Handling\Test\Data dans le dossier d’emplacement de réception nommé EAIProcess.RequestPort (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop).  
  
4.  Ce message est un fichier texte, et il provoquera une exception. Ouvrez le dossier nommé All_Exceptions (dans le dossier \Source\Samples\Exception Handling\Test\Filedrop), puis double-cliquez sur le message d’erreur pour l’ouvrir dans InfoPath à l’aide du modèle approprié. Vous verrez que le mécanisme de gestion des exceptions de ESB sérialise le contenu de façon appropriée pour permettre d’InfoPath à rendre.  
  
5.  Ensuite, copiez le fichier nommé .xml soapmessage [1] à partir du dossier \Source\Samples\Exception Handling\Test\Data dans le EAIProcess.RequestPort réception dossier d’emplacement.  
  
6.  Ce message est un document XML qui contient une section CDATA, et il provoquera une exception. Ouvrez le dossier de sortie All_Exceptions et double-cliquez sur le message d’erreur pour l’ouvrir dans InfoPath. Vous verrez que le mécanisme de gestion des exceptions de ESB Sérialise ce contenu correctement pour permettre d’InfoPath à rendre.  
  
7.  Pour finir, copiez le fichier nommé Csqzav01.pdf à partir du dossier \Source\Samples\Exception Handling\Test\Data dans le EAIProcess.RequestPort les emplacement de réception.  
  
8.  Ce message est un fichier PDF, et il provoquera une exception. Ouvrez le dossier de sortie All_Exceptions et double-cliquez sur le message d’erreur pour l’ouvrir dans InfoPath. Vous verrez que le mécanisme de gestion des exceptions de ESB sérialise et en Base 64 encode le contenu pour permettre d’InfoPath à restituer.
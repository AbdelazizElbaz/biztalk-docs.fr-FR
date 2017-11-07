---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: e31246cf90f42206de6a22fcc32338fcb2936db3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-receive-ports-in-tibco-enterprise-message-service"></a>Création de ports de réception pour TIBCO Enterprise Message Service
Les étapes suivantes permettent de créer un port de réception.  
  
### <a name="to-create-a-receive-port"></a>Pour créer un port de réception  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Ports de réception unidirectionnels**.  
  
3.  Dans le **propriétés du Port de réception** fenêtre, dans le **général** page, procédez comme suit :  
  
    1.  Dans le **nom** , tapez `ReceiveFromTIBCOEMS`.  
  
    2.  Dans le **authentification** zone de groupe, spécifiez le traitement des messages lors de l’utilisation de l’authentification.  
  
    3.  Sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher.  
  
4.  Sur le **emplacements de réception** page, procédez comme suit :  
  
    1.  Cliquez sur **Nouveau**.  
  
    2.  Dans le **emplacements de réception** fenêtre, dans le **général** , tapez le **nom** l’emplacement de réception.  
  
    3.  À partir de la **Type** liste déroulante, sélectionnez le type de transport et à partir de la **Gestionnaire de réception** liste déroulante, sélectionnez l’adresse de transport.  
  
    4.  À partir de la **pipeline de réception** liste déroulante, sélectionnez le pipeline de réception.  
  
    5.  Sur le **planification** page, sélectionnez le **date de début** et **date de fin** pour restreindre la réception des documents.  
  
    6.  Sélectionnez le **activer la fenêtre de service** case à cocher.  
  
    7.  Cliquez sur **OK**.  
  
5.  Sur le **mappages entrants** , sélectionnez les mappages entrants pour transformer les documents sur le port sélectionné.  
  
6.  Sur le **suivi** , sélectionnez le suivi des propriétés de message et le suivi des corps de message souhaité.  
  
7.  Cliquez sur **OK**.  
  

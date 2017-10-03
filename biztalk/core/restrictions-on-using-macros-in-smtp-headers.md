---
title: "Restrictions sur l’utilisation des Macros dans les en-têtes SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], restrictions
- macros, SMTP headers [SMTP adapters]
- SMTP adapters, macros
- SMTP adapters, restrictions
- configuring [SMTP adapters], SMTP headers
- SMTP adapters, SMTP headers
- configuring [SMTP adapters], macros
- SMTP headers
ms.assetid: ceab0917-cb3c-423b-a15f-63747ab1d8da
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5bf13f97d3cee4bf5930c448c3444aead898624
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restrictions-on-using-macros-in-smtp-headers"></a>Restrictions sur l’utilisation des Macros dans les en-têtes SMTP
Un ensemble de macros prédéfini permet de générer de manière dynamique les propriétés **Objet**, **À**, **De**et **Cc** de l'en-tête d'un message SMTP. Avant d'envoyer un message, le gestionnaire d'envoi SMTP remplace les macros d'un en-tête par leurs valeurs. Vous pouvez faire appel à plusieurs macros lors de la constitution d'un en-tête.  
  
 Le gestionnaire d'envoi SMTP ne remplace pas la macro dans la propriété d'en-tête **À**, **De**ou **Cc** si l'une des conditions suivantes est remplie :  
  
-   La propriété système correspondante n'est pas définie.  
  
-   La macro est mal orthographiée.  
  
-   La valeur de la macro contient des symboles d'en-têtes SMTP non valides.  
  
 Si une des conditions suivantes est remplie, l’envoi SMTP gestionnaire laisse les macros comme elles sont, par exemple, **%sourceparty%@somedomain.com**  ou **Message de %sourceparty%**.  
  
 Le tableau suivant répertorie les macros auxquelles vous pouvez faire appel pour générer les en-têtes **À**, **Cc**et **Objet** .  
  
|Macro|Description|Pour utilisation avec À|Pour utilisation avec Cc|Pour utilisation avec Objet|  
|-----------|-----------------|---------------------|---------------------|--------------------------|  
|%MessageID%|GUID (Globally Unique Identifier) du message dans BizTalk Server. La valeur provient de la propriété de contexte de message **BTS.MessageID**.|Non|Non|Oui|  
|%datetime_bts2000%|Date et heure UTC au format AAAAMMJJhhmmsss, où sss correspond aux secondes et aux millisecondes (par exemple, 199707121035234 signifie 1997/07/12, 10:35:23 et 400 millisecondes).|Non|Non|Oui|  
|%datetime%|Date et heure UTC au format AAAA-MM-JJThhmmss (par exemple, 1997-07-12T103508).|Non|Non|Oui|  
|%datetime.tz%|Heure et date locales ainsi que le fuseau horaire GMT au format AAAA-MM-JJThhmmssTZD (par exemple, 1997-07-12T103508+800).|Non|Non|Oui|  
|%time%|Heure UTC au format hhmmss.|Non|Non|Oui|  
|%time.tz%|Heure locale ainsi que le fuseau horaire GMT au format hhmmssTZD (par exemple, 124525+530).|Non|Non|Oui|  
|%SourceParty%|Nom du tiers source qui a envoyé le message à l'adaptateur FILE.|Non|Non|Oui|  
|%SourcePartyQualifier%|Qualificateur du tiers source qui a envoyé le message à l'adaptateur FILE.|Non|Non|Oui|  
|%DestinationParty%|Nom du tiers de destination. La valeur provient de la propriété de contexte de message **BTS.DestinationParty**.|Oui|Oui|Oui|  
|%DestinationPartyQualifier%|Qualificateur du tiers de destination. La valeur provient de la propriété de contexte de message **BTS.DestinationPartyQualifier**.|Non|Non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions relatives à la configuration de l’adaptateur SMTP](../core/restrictions-when-configuring-the-smtp-adapter.md)
---
title: AS2 Les Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fac8418-3c07-4513-94aa-e7a25087d789
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09c2d2d922b9a7ed8a9dfd1ea4c64c369d0e9d2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-messages"></a>Messages AS2
Cette rubrique décrit un message AS2, sa structure, ses propriétés de contexte et ses en-têtes.  
  
## <a name="structure-of-an-as2-message"></a>Structure d'un message AS2  
 Dans [!INCLUDE[prague](../includes/prague-md.md)], les messages AS2 sont structurés selon [RFC 4130, « basé sur MIME sécurisé pair à pair de données commerciales échange via HTTP, Applicability Statement 2 (AS2)](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/? LinkID = 184212](http://go.microsoft.com/fwlink/?LinkID=184212)).  
  
 La structure élémentaire d'un message AS2 est au format MIME dans un message HTTP avec des en-têtes AS2 spécifiques supplémentaires. La nature du message sous les en-têtes HTTP, AS2 et MIME dépend du type du message :  
  
-   **Signé** – si le message est signé, un wrapper de signature est ajouté autour de la charge du document.  
  
-   **Compressé** – si le message est compressé, un wrapper de compression est ajouté aux charges du document et de signature.  
  
-   **Chiffré** – si le message est chiffré, un wrapper de chiffrement est ajouté aux charges du document, la signature et la compression.  
  
 La structure d'un message AS2, basé sur le chiffrement, la signature et la compression est indiquée dans le tableau ci-dessous.  
  
|Options de message AS2|Structure de message|  
|-------------------------|-----------------------|  
|-Aucune compression<br /><br /> -Aucun chiffrement<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header      EDI/XML Payload`|  
|-Compressé<br /><br /> -Aucun chiffrement<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           EDI/XML Payload (compressed)`|  
|-Connecté<br /><br /> -Aucune compression<br /><br /> -Aucun chiffrement|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           EDI/XML Payload           CMS-PKCS7 Signature`|  
|-Connecté<br /><br /> -Compressé<br /><br /> -Aucun chiffrement|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|-Chiffré<br /><br /> -Aucune compression<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           EDI/XML Payload (encrypted)`|  
|-Compressé<br /><br /> -Chiffré<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                EDI/XML Payload (compressed)(encrypted)`|  
|-Chiffré<br /><br /> -Connecté<br /><br /> -Aucune compression|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|-Compressé<br /><br /> -Chiffré<br /><br /> -Connecté|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
 Si la charge du document se compose de plusieurs documents, ils sont stockés dans une enveloppe MIME multipart/related comme décrit dans RFC 2387. Un en-tête MIME à disposition de contenu peut être utilisé pour spécifier le nom de fichier de chaque document dans le message.  
  
 Le tableau suivant illustre la structure d'un message AS2 qui contient plusieurs pièces jointes, basé sur les options de chiffrement de message, de signature et de compression.  
  
|Options de message AS2|Structure de message|  
|-------------------------|-----------------------|  
|-Aucune compression<br /><br /> -Aucun chiffrement<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header      MIME Multipart/related           EDI/XML Payloads`|  
|-Compressé<br /><br /> -Aucun chiffrement<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header      PKCS7-MIME Compression           MIME Multipart/related                EDI/XML Payload (compressed)`|  
|-Connecté<br /><br /> -Aucune compression<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header       MIME Security Multipart (signed)           MIME Multipart/related                EDI/XML Payload           CMS-PKCS7 Signature`|  
|-Compressé<br /><br /> -Connecté<br /><br /> -Aucun chiffrement|`HTTP, AS2, MIME Header       PKCS7-MIME Compression           MIME Security Multipart (signed)(compressed)                MIME Multipart/related (compressed)                     EDI/XML Payload (compressed)                CMS-PKCS7 Signature (compressed)`|  
|-Chiffrement<br /><br /> -Aucune compression<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Multipart/related (encrypted)                EDI/XML Payload (encrypted)`|  
|-Compressé<br /><br /> -Chiffré<br /><br /> -Aucune signature|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Multipart/related                     EDI/XML Payload (compressed)(encrypted)`|  
|-Chiffré<br /><br /> -Connecté<br /><br /> -Aucune compression|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           MIME Security Multiparts (signed)(encrypted)                MIME Multipart/related                     EDI/XML Payload (encrypted)                CMS-PKCS7 Signature (encrypted)`|  
|-Compressé<br /><br /> -Chiffré<br /><br /> -Connecté|`HTTP, AS2, MIME Header       CMS-PKCS7 MIME Encryption           PKCS7-MIME Compression (encrypted)                MIME Security Multiparts (signed)(compressed)(encrypted)                     MIME Multipart/related                          EDI/XML Payload (compressed)(encrypted)                     CMS-PKCS7 Signature (compressed)(encrypted)`|  
  
## <a name="as2-context-properties"></a>Propriétés de contexte AS2  
 Les propriétés de contexte utilisées pour traiter le message AS2 incluent les propriétés qui peuvent être promues et celles qui ne sont pas exposées publiquement, mais peuvent être vues dans les messages suspendus et suivis. Pour obtenir la liste des propriétés de contexte AS2, consultez [propriétés de contexte AS2](../core/as2-context-properties.md).  
  
## <a name="as2-headers"></a>En-têtes AS2  
 Les en-têtes AS2 des messages AS2 décrivent les tiers destinataire et expéditeur et fournissent les informations nécessaires au tiers destinataire pour envoyer une réponse MDN. La partie réceptrice utilisera les en-têtes MDN, sauf si le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété est sélectionnée dans l’accord AS2, ou si les informations ne sont pas disponibles dans l’accord Propriétés.  
  
 Les en-têtes AS2-From et AS2-To et la propriété de contexte MessageID décrivent de façon unique un message AS2. Ils permettent également de mettre en corrélation un MDN et le message AS2 de réponse.  
  
 Les en-têtes sont répertoriés (dans l'ordre alphabétique) dans le tableau suivant :  
  
|En-tête AS2|Obligatoire/Facultatif|Valeurs|  
|----------------|------------------------|------------|  
|AS2-Version|Ce paramètre est facultatif|"1.1"|  
|AS2-From|Requis|Nom de la société qui envoie le message AS2.<br /><br /> Valeurs : chaîne, ASCII imprimable, de 1 à 128 caractères de long|  
|AS2-To|Requis|Nom de la société à laquelle le message AS2 est envoyé.<br /><br /> Valeurs : chaîne, ASCII imprimable, de 1 à 128 caractères de long|  
|Texte AS2|Requis|Texte (dans cet en-tête dans le message)<br /><br /> Valeurs : chaîne, ASCII imprimable, de 1 à 128 caractères de long|  
|Disposition-Notification-To|Requis|Le cas échéant, sert de requête pour un MDN à renvoyer. Si accompagné d'un en-tête receipt-delivery-option, il s'agit d'une requête pour un MDN  asynchrone. Sinon, il s'agit d'une requête pour un MDN synchrone.<br /><br /> En cas d'absence, aucun MDN n'est requis.<br /><br /> Valeur : adresse de messagerie. L'adresse ne doit cependant pas être utilisée pour identifier où retourner le MDN. L'application destinataire doit ignorer l'adresse de messagerie et ne doit pas contester les violations de syntaxe d'adresse.|  
|EDIINT - Fonctionnalités|Requis|Indique les fonctionnalités prises en charge par le système émetteur. BizTalk utilise cet en-tête pour indiquer la prise en charge de plusieurs pièces jointes.<br /><br /> Valeur : “MA”|  
|Receipt-Delivery-Option|Requis|Indique l'URL à laquelle le MDN doit être envoyé. En présence de Receipt-Delivery-Option, Disposition-notification-to sert de requête pour un MDN asynchrone. Receipt-Delivery-Option doit toujours être accompagné par Disposition-Notification-To.<br /><br /> En l'absence de Receipt-Delivery-Option et en présence de Disposition-notification-to, Disposition-notification-to sert de requête pour un MDN synchrone.<br /><br /> Valeurs : chaîne URL.|  
|signed-receipt-protocol<br /><br /> (dans Disposition-Notification-Options)|Ce paramètre est facultatif|Défini sur « pcks7-signature », permet de demander un accusé de réception signé au tiers expéditeur et indique le format dans lequel l'accusé de réception signé doit être retourné au demandeur.<br /><br /> Valeurs : facultatif, pcks7-signature|  
|signed-receipt-micalg<br /><br /> (dans Disposition-Notification-Options)|Ce paramètre est facultatif|Liste des algorithmes MIC utilisés de préférence par le demandeur pour signer le reçu renvoyé. La liste des algorithmes MIC doit être respectée par le tiers destinataire de gauche à droite.<br /><br /> Valeurs : facultatif, MD5 ou SHA1|  
  
 Pour les messages entrants, les pipelines de réception AS2EdiReceive et AS2Receive valident les valeurs de l'algorithme Signed Receipt Protocol et Signed Receipt MIC à partir des propriétés de l'accord AS2.  
  
 Pour les messages AS2 sortants, les pipelines d'envoi AS2EdiSend et AS2Send complètent les en-têtes AS2 ci-dessus à partir des valeurs entrées dans l'accord AS2 (à l'exception de AS2-Version, codé en dur sous la forme 1.1).  
  
 **Demande de MDN**  
  
 La demande pour que le tiers destinataire retourne un MDN (Message Disposition Notification) est effectuée en plaçant l'en-tête suivant dans le message à envoyer :  
  
 En-tête-requête-MDN = "Disposition-notification-to"  ":"  adresse-messagerie  
  
 L'adresse de messagerie ne doit pas être utilisée pour identifier où retourner le MDN. Les applications destinataires doivent ignorer la valeur et ne pas publier d'erreur concernant les violations de syntaxe d'adresse.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages MDN](../core/mdn-messages.md)
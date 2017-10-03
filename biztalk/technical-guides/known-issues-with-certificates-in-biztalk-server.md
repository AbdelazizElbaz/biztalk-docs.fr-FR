---
title: "Problèmes connus avec les certificats dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab58264b-2475-4831-9f08-bfbaa293022f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5aecfca9f58758e72f357439901684a0a617f3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-certificates-in-biztalk-server"></a>Problèmes connus avec les certificats dans BizTalk Server
Cette section décrit les problèmes connus avec la gestion des certificats numériques sont utilisés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="general-certificate-issues"></a>Problèmes généraux de certificat  
  
### <a name="lack-of-connectivity-to-the-certificate-revocation-list-will-cause-a-certificate-to-be-rejected"></a>Absence de connectivité à la liste de révocation de certificats entraîne un certificat soient rejetées  
 Ce problème concerne l’erreur suivante : « une erreur d’authentification est survenu. L’état de l’autorité de certification (CA) qui a émis le certificat utilisé pour signer le message est inconnu. » Cette erreur peut se produire même lorsque le certificat de signature est valide lorsqu’ils sont affichés dans la console MMC (à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisateur) sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Cette condition peut se produire si la propriété « Vérification de révocation de certificats » est activée sur le composant décodeur S/MIME dans le pipeline de réception. Lorsque cette propriété est définie sur true, BizTalk Server va tenter d’interroger la liste de révocation de certificats (CRL) pour voir si le certificat entrant a été révoqué. Si le certificat proprement dit n’est pas révoqué n’a pas d’importance. Si BizTalk Server ne peut pas interroger la liste de révocation correspondant en raison de problèmes de connectivité, il n’acceptera pas le certificat. Pour résoudre cette erreur, afficher les propriétés du certificat en double-cliquant sur le certificat que vous avez utilisé. Dans l’onglet Détails, vous verrez l’attribut « Point de Distribution CRL » dans la liste de champs. Il doit y avoir plusieurs URL qui pointent vers la liste de révocation sur votre serveur d’autorité de certification dans cet attribut. Le serveur BizTalk server doit être en mesure d’accéder à toutes les URL de récupérer la liste de révocation. Dans le cas contraire, la vérification de révocation échoue et l’erreur ci-dessus sera publiée.  
  
### <a name="the-other-people-certificate-store-is-not-initialized-until-accessed"></a>Le magasin de certificats d’autres personnes n’est pas initialisé qu’après l’accès  
 Ce problème concerne l’erreur du magasin de certificats suivante lorsque vous essayez d’ajouter ou modifier l’envoi/ports/emplacements de réception à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à distance de la console administrateur : « Impossible d’ouvrir le magasin de certificats ». et « le système ne peut pas trouver le fichier spécifié. (Système) ».  
  
> [!NOTE]  
>  Vous pouvez modifier ces artefacts à l’aide de la console d’administration si vous vous connectez directement à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Sur un ordinateur nouvellement installé, le **certificats d’autres personnes** magasin n’est pas initialisé, sauf si vous y accéder une seule fois. Lors de la configuration du groupe, vous pouvez initialiser cette **certificats d’autres personnes** stocker et par conséquent ne voient pas cette erreur sur un ordinateur sur le groupe auquel la configuration a été effectuée.  
  
### <a name="biztalk-server-only-supports-one-personal-certificate-for-each-biztalk-group"></a>BizTalk Server prend uniquement en charge un seul certificat personnel pour chaque groupe BizTalk  
 Le certificat personnel qui est utilisé par le groupe BizTalk est spécifié en définissant l’empreinte numérique du certificat personnel dans les propriétés du groupe BizTalk. Un groupe BizTalk peut représenter une entreprise, un service, un concentrateur ou une autre division.  
  
## <a name="as2-certificate-issues"></a>AS2 Problèmes de certificat  
  
### <a name="the-as2-decoder-will-not-validate-that-a-certificate-is-configured-on-the-host-or-for-the-destination-party"></a>Le décodeur AS2 ne validera pas qu’un certificat est configuré sur l’ordinateur hôte ou pour le tiers de destination  
 Le décodeur AS2 déchiffre un message à condition que le certificat privé relatif à ce dernier soit configuré dans le magasin de certificats. En revanche, le décodeur AS2 ne valide pas le fait que le certificat de déchiffrement soit identique au certificat configuré sur l'hôte. Le message reçu peut être chiffré avec plusieurs certificats.  
  
### <a name="biztalk-server-will-be-unable-to-decrypt-a-message-saved-in-wire-format-if-the-certificate-is-not-valid"></a>BizTalk Server ne pourra pas déchiffrer un message enregistré au format câble si le certificat n’est pas valide  
 **Symptôme**  
  
 BizTalk Server ne peut pas déchiffrer un message AS2 entrant enregistré au format câble dans la base de données de non-répudiation.  
  
 **Cause possible**  
  
 Le certificat requis pour déchiffrer le message a expiré ou été révoqué. La probabilité que cela se produise est supérieure si une certaine période s'est écoulée depuis l'enregistrement du message AS2 dans la base de données de non-répudiation. Si cela ce produit, il se peut que vous n'ayez pas d'accès immédiat à un certificat valide pour le message.  
  
 **Résolution**  
  
 Acquérir un certificat valide pour le déchiffrement du message.  
  
### <a name="if-an-as2-message-cannot-be-decrypted-the-problem-may-be-fixed-by-re-importing-the-certificate"></a>Si un message AS2 ne peut pas être déchiffré, le problème peut être résolu en réimportant le certificat  
 **Symptôme**  
  
 Le décodeur AS2 rencontre une exception lorsqu’il tente de déchiffrer un message AS2, qui lève l’erreur suivante :  
  
```  
"The AS2 Decoder encountered an exception during processing. Details of the message and exception are as follows:   
   AS2-From:"PARTNER" AS2-To:"HOME" MessageID:"<137706.1178060412333@servername>"   
   MessageType: "unknown" Exception:"An error occurred when decrypting an AS2 message."  
System.ArgumentNullException: Value cannot be null.  
Parameter name: PayloadContentType  
at Microsoft.BizTalk.Edi.Reporting.Common.Utilities.ValidateArgument(Object o,  
String parameterName, Boolean isEmptyStringValidationRequired)  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.ValidateParameters()  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.Create()"  
  
```  
  
 **Cause possible**  
  
 Le certificat utilisé pour déchiffrer le message AS2 doit être rechargée dans le magasin personnel.  
  
 **Résolution**  
  
 Supprimer le certificat existant dans le magasin personnel et réimporter le certificat dans le magasin personnel à l’aide de l’Assistant Importation de certificat. Faire en cliquant sur le **certificat** dossier sous le **magasin personnel**, en pointant sur **toutes les tâches**, puis en cliquant sur **importation**.  
  
### <a name="use-the-same-logon-for-the-in-process-host-instance-and-the-isolated-host-instance-to-ensure-that-personal-store-is-recognized"></a>Utiliser le même nom de connexion pour l’instance hôte in-process et l’instance d’hôte isolé pour vous assurer que le magasin personnel est reconnu.  
 Le magasin de certificats Personnels sera disponible pour le traitement des messages uniquement si le profil utilisateur est chargé pour l'utilisateur dont les informations d'identification sont associées à l'instance hôte. Le magasin Personnel est utilisé pour les certificats de signature et de déchiffrement (la clé propre privée de l'utilisateur). Le profil utilisateur est chargé par défaut pour l'instance hôte In-process ; toutefois, il n'est pas chargé par défaut pour l'instance hôte isolé. Vous pouvez faire en sorte qu'une application charge le profil utilisateur pour l'hôte isolé.  Vous pouvez également contourner ce problème en utilisant le même nom de connexion pour l'instance hôte In-process et l'instance hôte isolé.  
  
 Plutôt que de faire charger le profil utilisateur par une application, vous pouvez créer un service vide pour charger le profil. Pour plus d’informations sur la création d’un service vide, consultez [Comment : créer des Services Windows](http://go.microsoft.com/fwlink/?LinkId=155149) (http://go.microsoft.com/fwlink/?LinkId=155149) dans l’aide de Visual Studio.  
  
 Après avoir créé le service vide pour charger le profil, procédez comme suit :  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **exécuter** pour ouvrir le **exécuter** boîte de dialogue.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **service.msc** et appuyez sur **entrée** pour ouvrir le **Services** le composant logiciel enfichable MMC.  
  
3.  Ouvrez le **propriétés** boîte de dialogue pour le service que vous avez créé. Le service d’avec le bouton droit et sélectionnez **propriétés**.  
  
4.  Cliquez sur le **session** onglet, sélectionnez **ce compte**, puis entrez le nom d’ouverture de session utilisé pour l’instance d’hôte isolé.  
  
5.  Cliquez sur **OK**.  
  
6.  Démarrez manuellement le service pour charger le profil utilisateur pour cet utilisateur d’ouverture de session.  
  
### <a name="the-key-usage-attribute-of-a-certificate-must-match-the-certificates-use"></a>L'attribut Utilisation de la clé d'un certificat doit correspondre à l'utilisation du certificat  
 Les certificats utilisés pour le transport AS2 doivent avoir les attributs requis pour l'utilisation prévue. Pour la signature et la vérification de signature, l'attribut Utilisation de la clé du certificat doit être défini sur Signature numérique. Pour le chiffrement et le déchiffrement, l'attribut Utilisation de la clé du certificat doit être défini sur Chiffrement des données ou Chiffrement de clés. Vous pouvez vérifier l’attribut utilisation de la clé en double-cliquant sur le certificat, cliquez sur le **détails** onglet dans le **certificat** boîte de dialogue et en vérifiant la **utilisation de la clé** champ .  
  
### <a name="the-certificate-resolution-list-will-be-verified-for-an-outgoing-mdn-if-the-as2-to-property-is-not-set-for-the-party"></a>La liste de résolution des certificats est vérifiée pour un MDN sortant si la propriété AS2-To n'est pas définie pour le tiers  
 Dans l'accord par défaut pour un MDN sortant, la vérification de la liste de résolution des certificats est effectuée. Si vous ne voulez pas que cette vérification ait lieu, vérifiez que la propriété AS2-To correcte est définie, de façon à ce que le tiers qui reçoit puisse être résolu et les propriétés du tiers déterminées. Si c'est le cas, l'accord par défaut qui invite à vérifier la liste de résolution des certificats n'est pas utilisé. Vous devez également désactiver la propriété Vérifier la liste de révocation des certificats de la page Général des propriétés de tiers AS2.
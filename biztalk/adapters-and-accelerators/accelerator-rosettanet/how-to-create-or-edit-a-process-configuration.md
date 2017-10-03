---
title: "Comment créer ou modifier une Configuration de processus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- authorization properties
- non-repudiation, properties
- creating, process configuration
- modifying, process configuration
ms.assetid: ef6160f1-f2f0-42ff-a516-7818c9d79d26
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4c9c9be5e9f3361683e495febbd98a05156399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-or-edit-a-process-configuration"></a>Comment créer ou modifier une configuration de processus
Cette rubrique décrit comment créer ou modifier une configuration de processus.  
  
 Les paramètres de la configuration de processus sont indiqués dans le tableau suivant, organisés par onglet. Les procédures de création et de modification d'une configuration de processus sont décrites à la suite du tableau.  
  
 Les propriétés d'autorisation et de non-répudiation sont interdépendantes. Pour plus d’informations sur la façon de définir ces propriétés, consultez [d’autorisation et de propriétés de Non répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).  
  
|Onglet|Paramètre|Utilisation|  
|---------|-------------|-----------|  
|**Général**|**Afficher le Code**|Code d'affichage du PIP (Partner Interface Process). Il peut s'agir de la désignation PIP de RosettaNet ou du nom d'un schéma personnalisé. Il est recommandé d'utiliser une convention d'affectation de noms standard comme un nom contenant le code de processus et la version, par exemple, « STD_3A2_R02.00.00A ». Vous pouvez ainsi plus facilement gérer des versions différentes du même PIP.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Code de processus**|Le code PIP à trois chiffres. Par exemple, « 3A2 ».<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Version**|Version du PIP. Par exemple, « V02.02 » ou « R02.00.00A ».<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Nom du processus**|Nom du PIP. Par exemple, « Action de demande de prix et de disponibilité ».<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Description**|Description des messages conformes au PIP.|  
|**Général**|**Standard**|Type de norme.<br /><br /> Valeurs possibles : RosettaNet (valeur par défaut) ou CIDX|  
|**Général**<br /><br /> (Zone Contenu non RosettaNet)|**Message standard**|Pour du contenu non RosettaNet, nom de la norme non RosettaNet. Utilisez ce paramètre si vous n'utilisez pas de PIP RosettaNet, mais que vous avez défini un schéma personnalisé. Utilisez ce paramètre pour RNIF 2.0 uniquement et non pour RNIF 1.1 ou CIDX.|  
|**Général**<br /><br /> (Zone Contenu non RosettaNet)|**Version de la norme**|Pour du contenu non RosettaNet, version de la norme non RosettaNet. Utilisez ce paramètre si vous n'utilisez pas de PIP RosettaNet, mais que vous avez défini un schéma personnalisé. Utilisez ce paramètre pour RNIF 2.0 uniquement et non pour RNIF 1.1 ou CIDX.|  
|**Général**<br /><br /> (Zone Contenu non RosettaNet)|**ID de liaison de charge utile**|Pour du contenu non RosettaNet, numéro d'identification du contenu de charge utile. Utilisez ce paramètre si vous n'utilisez pas de PIP RosettaNet, mais que vous avez défini un schéma personnalisé. La partie qui implémente le PIP personnalisé doit définir cette valeur. Utilisez ce paramètre pour RNIF 2.0 uniquement et non pour RNIF 1.1 ou CIDX.|  
|**Activité**<br /><br /> (Zone Accusé de réception)|**Non-répudiation obligatoire**|Détermine si les messages de signal doivent être signés (avec un résumé de message inclus dans le message d’accusé de réception) et stockés dans leur format d’origine par le destinataire de la table MessageStorageIn ou MessageStorageOut de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]base de données d’Archive, à des fins de non-répudiation. Le destinataire doit stocker les signaux pour la période désignée dans la propriété **Non répudiation de l'origine** dans la configuration du partenaire.<br /><br /> Les valeurs possibles : `True` (la valeur par défaut) ou`False`<br /><br /> Si la valeur est `False`, les messages de signal ne sont pas stockés à des fins de non-répudiation. Les messages de signal peuvent être signés ou non.<br /><br /> Si la valeur est `True`, les messages de signal entrants sont stockés dans leur format d'origine dans la table MessageStorageIn. Les messages de signal sortants sont stockés dans leur format d'origine dans la table MessageStorageOut. Les messages de signal doivent être signés.<br /><br /> Pour plus d’informations, consultez [d’autorisation et de propriétés de Non répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activité**<br /><br /> (Zone Accusé de réception)|**Moment de l’accusé de réception (secondes)**|Durée en secondes pendant laquelle l'initiateur doit recevoir l'accusé de réception. Si l'initiateur ne le reçoit dans ce délai, il fait une nouvelle tentative jusqu'à ce qu'il atteigne le nombre de **Nouvelles tentatives** maximal (indiqué dans la section **Comportement** de cet onglet).<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]mesures la **moment de l’accusé de réception** la valeur de l’heure de l’initiateur envoyé le message d’action avec succès. La valeur est incluse dans l'en-tête de remise. La valeur ne peut pas être inférieure à zéro ou supérieure à celle de la **Durée d'exécution** définie dans la même page.<br /><br /> Vous utilisez ce paramètre pour les messages de signal (accusés de réception d'application) retournés dans le traitement RNIF 1.1 et 2.01. Vous utilisez également ce paramètre pour les accusés de réception d'acceptation retournés dans le traitement RNIF 1.1.<br /><br /> La valeur par défaut est 7 200 secondes (deux heures).|  
|**Activité**<br /><br /> (Zone Comportement)|**Une autorisation est requise**|Détermine si un message d'action ou de signal entrant doit être signé. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]n’accepte pas un document commercial si la personne/le rôle n’est pas autorisé à effectuer l’activité.<br /><br /> Les valeurs possibles : `True` (la valeur par défaut) ou`False`<br /><br /> Si la valeur est `False`, les messages d'action et de signal sortants ne sont pas signés. Les messages d'action et de signal entrants peuvent être signés. S'ils ne sont pas signés, le système autorise le partenaire via l'en-tête de remise.<br /><br /> Si la valeur est `True`, les messages entrants doivent être signés. Les messages sortants peuvent être signés. Les messages sortants sont signés uniquement si la valeur de **Non-répudiation de l'origine et du contenu** est `True`.<br /><br /> Pour plus d’informations, consultez [d’autorisation et de propriétés de Non répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activité**<br /><br /> (Zone Comportement)|**Confidentialité persistante requise**|Détermine si le chiffrement est requis.<br /><br /> Valeurs possibles : **Aucun** (valeur par défaut) indique qu'aucun chiffrement n'est nécessaire. **Charge utile** indique que le chiffrement du contenu de service et des pièces jointes est requis. **Conteneur de charge utile** indique que le chiffrement du contenu de service, des pièces jointes et de l'en-tête de service est requis.<br /><br /> Dans RNIF 2.0, les en-têtes de préambule et de remise ne sont jamais chiffrés. Dans RNIF 1.1, aucune partie de message n'est chiffrée. Elles sont seulement signées.|  
|**Activité**<br /><br /> (Zone Comportement)|**Transport sécurisé requis**|Détermine si le transport HTTPS est requis.<br /><br /> Les valeurs possibles : `True` (la valeur par défaut) ou`False`|  
|**Activité**<br /><br /> (Zone Comportement)|**Action unique**|Détermine si les messages ont une action unique ou double.<br /><br /> Les valeurs possibles : `True` (la valeur par défaut) ou`False`<br /><br /> Les messages d'action unique sont la Distribution d'informations ou la Notification. Les messages de double action sont la Transaction commerciale, la Confirmation de demande, la Demande/Réponse ou la Requête/Réponse.<br /><br /> Si la norme est CIDX, **Action unique** doit avoir la valeur **True**.|  
|**Activité**<br /><br /> (Zone Comportement)|**Est synchrone**|Détermine si des partenaires commerciaux échangent des messages d'action de façon synchrone ou asynchrone.<br /><br /> Valeurs possibles : `True` ou `False`(valeur par défaut)<br /><br /> Non utilisé pour RNIF 1.1.|  
|**Activité**<br /><br /> (Zone Comportement)|**Non-répudiation de l’origine et de contenu**|Détermine si les messages d'action doivent être signés et stockés dans leur format de réception d'origine par le destinataire dans la table MessageStorageIn ou MessageStorageOut de la base de données BTARNArchive, à des fins de non-répudiation. Le destinataire doit stocker les messages d'action pour la période désignée dans la propriété **Non-répudiation de l'origine** dans la configuration du partenaire à des fins de non-répudiation. Si nécessaire, les messages d'action doivent être signés.<br /><br /> Les valeurs possibles : `True` (la valeur par défaut) ou`False`<br /><br /> Si la valeur est `False`, les messages d'action ne sont pas stockés à des fins de non-répudiation. Les messages d'action peuvent être signés ou non.<br /><br /> Si la valeur est `True`, les messages d'action entrants sont stockés dans leur format d'origine dans la table MessageStorageIn. Les messages d'action sortants sont stockés dans leur format d'origine dans la table MessageStorageOut. Les messages d'action doivent être signés.<br /><br /> Pour plus d’informations, consultez [d’autorisation et de propriétés de Non répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md).|  
|**Activité**<br /><br /> (Zone Comportement)|**Nombre de tentatives**|Nombre de fois que le processus doit réessayer l'activité en cas d'échec du transport ou du traitement. Si le nombre de nouvelles tentatives est 3, le processus tente l'activité quatre fois.<br /><br /> La valeur par défaut est 3.<br /><br /> Si la communication est synchrone, puis [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] n’utilise pas ce champ, car les nouvelles tentatives ne s’appliquent pas aux transactions synchrones.|  
|**Activité**<br /><br /> (Zone Comportement)|**Temps pendant l’exécution**|Période (en secondes) pendant laquelle le processus doit exécuter l'activité. La période commence quand l'initiateur envoie le premier document. L'initiateur (et non le répondeur) doit s'assurer que l'activité est exécutée pendant cette période. Cette valeur figure dans l'en-tête de remise.<br /><br /> La valeur par défaut est 86 400 secondes (24 heures).<br /><br /> La valeur de la **Durée d'exécution** doit être supérieure à celle du **Délai de l'accusé de réception** définie dans la section **Accusé de réception** de la même page.|  
|**Activité**<br /><br /> (Zone Général)|**Type**|Détermine le type d'activité.<br /><br /> Valeurs possibles : **Transaction commerciale**, **Distribution d'informations** (valeur par défaut), **Notification**, **Requête/Réponse**, **Demande/Confirmation**ou **Demande/Réponse**|  
|**Initiateur**<br /><br /> (Zone Document commercial)|**Description**|Description du document commercial de l'action de l'initiateur.|  
|**Initiateur**<br /><br /> (Zone Document commercial)|**Nom**|Nom du document commercial de l'action de l'initiateur. Par exemple, « Demande de prix et de disponibilité ».|  
|**Initiateur**<br /><br /> (Zone Document commercial)|**Version**|Version du document commercial. Par exemple, « V02_02_00 » ou « R02.00.00A ».<br /><br /> Vous pouvez trouver ce numéro de version au début du fichier .htm de recommandations pour les messages XML RosettaNet que vous téléchargez avec le fichier .doc de spécification PIP et la définition de type de document (DTD) PIP de l'organisation RosettaNet.|  
|**Initiateur**<br /><br /> (Zone Général)|**Action**|Description de l'action de l'initiateur. Par exemple, « Action de requête de test synchrone ».|  
|**Initiateur**<br /><br /> (Zone Général)|**Rôle**|Rôle de l'initiateur. Par exemple, « Acheteur » ou « Payeur ».<br /><br /> La valeur par défaut est « Initiateur ».|  
|**Initiateur**<br /><br /> (Zone Général)|**Description du rôle**|Description du rôle de l'initiateur. Par exemple, « Tiers émettant le paiement ».|  
|**Initiateur**<br /><br /> (Zone Général)|**Type de rôle**|Type de rôle de l'initiateur.<br /><br /> Valeurs possibles : **Organisationnel**, **Employé**ou **Fonctionnel** (valeur par défaut)|  
|**Initiateur**<br /><br /> (Zone Général)|**Service**|Service de l'initiateur. Par exemple, « Service de l'acheteur » ou « Service du payeur ».|  
|**Initiateur**<br /><br /> (Zone Général)|**Classification du service**|Type de service de l'initiateur. Par exemple, « Service commercial ».|  
|**Répondeur**<br /><br /> (Zone Document commercial)|**Description**|Description du document commercial de l'action du répondeur. Par exemple, « Confirme formellement l'état des éléments de ligne dans un bon de commande ».|  
|**Répondeur**<br /><br /> (Zone Document commercial)|**Nom**|Nom du document commercial de l'action du répondeur. Par exemple, « Confirmation de bon de commande ».|  
|**Répondeur**<br /><br /> (Zone Document commercial)|**Version**|Version du document commercial. Par exemple, « V02.02.00 » ou « R02.00.00A ». Vous pouvez trouver ce numéro de version au début du fichier .htm de recommandations pour les messages XML RosettaNet que vous téléchargez avec le fichier .doc de spécification PIP et la définition de type de document (DTD) PIP de l'organisation RosettaNet.|  
|**Répondeur**<br /><br /> (Zone Général)|**Action**|Description de l'action du répondeur. Par exemple, « Action de confirmation de bon de commande ».|  
|**Répondeur**<br /><br /> (Zone Général)|**Rôle**|Rôle du répondeur. Par exemple, « Vendeur ».<br /><br /> La valeur par défaut est « Répondeur ».|  
|**Répondeur**<br /><br /> (Zone Général)|**Description du rôle**|Description du rôle du répondeur. Par exemple, « Tiers recevant le paiement ».|  
|**Répondeur**<br /><br /> (Zone Général)|**Type de rôle**|Type de rôle du répondeur.<br /><br /> Valeurs possibles : **Organisationnel** (valeur par défaut), **Employé**ou **Fonctionnel**|  
|**Répondeur**<br /><br /> (Zone Général)|**Service**|Service du répondeur. Par exemple, « Service du vendeur ».|  
|**Répondeur**<br /><br /> (Zone Général)|**Classification du service**|Type de service du répondeur. Par exemple, « Service commercial ».|  
  
### <a name="to-implement-a-new-process-configuration"></a>Pour implémenter une nouvelle configuration de processus  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Cliquez avec le bouton droit sur **Paramètres de configuration du processus**, pointez sur **Nouveau**, puis cliquez sur **Configuration du processus**.  
  
4.  Dans la boîte de dialogue Propriétés de la nouvelle configuration de processus, sous les onglets **Général**, **Activité**, **Initiateur**et **Répondeur** , tapez des valeurs pour les paramètres indiqués dans le tableau précédent, puis cliquez sur **OK**.  
  
### <a name="to-edit-a-process-configuration"></a>Pour modifier une configuration du processus  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Cliquez sur **Paramètres de configuration du processus**.  
  
4.  Cliquez avec le bouton droit sur la configuration de processus à modifier, puis cliquez sur **Propriétés**.  
  
5.  Dans le  *\<configuration du processus >* boîte de dialogue de propriétés la **général** et **propriétés Contact** onglets, modifiez les paramètres en fonction des besoins. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour créer une Configuration de processus à l’aide de la spécification PIP](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)   
 [Propriétés d’autorisation et de non-répudiation](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)   
 [Paramètre des CIDX chem échange de messages](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [Administration de la Configuration de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)
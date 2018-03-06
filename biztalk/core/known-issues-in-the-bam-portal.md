---
title: "Problèmes connus avec le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e681e910-c664-479c-86f3-a6ae0ec97775
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cbfa298590c62b359045b6c7372501d8ef397e
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="known-issues-in-the-bam-portal"></a>Problèmes connus dans le portail BAM
Cette rubrique contient des informations destinées à vous aider à identifier et à résoudre les problèmes que vous pouvez rencontrer lorsque vous utilisez le portail BAM.  
  
## <a name="errors-occur-when-the-bam-portal-and-ie-are-on-the-same-computer-and-security-settings-are-low"></a>Erreurs se produisent lorsque le portail BAM et Internet Explorer sont sur le même ordinateur et les paramètres de sécurité faible  
 **Problème**  
  
 Lorsque vous utilisez Internet Explorer, vous pouvez rencontrer le message d’erreur **erreur serveur dans ' / BAM' Application** dans les circonstances suivantes :  
  
-   Lorsque vous cliquez sur une activité associée qui pointe vers une instance d'activité inexistante  
  
-   Tout en cliquant sur le **enregistrer l’alerte** bouton dans le scénario suivant :  
  
    -   Vous créez une requête sur le **ActivitySearch** page, puis cliquez sur **définir l’alerte**.  
  
    -   Vous renseignez les champs d’alerte, puis sur **enregistrer l’alerte**.  
  
    -   Vous cliquez sur le bouton Précédent.  
  
    -   Vous cliquez sur le **enregistrer l’alerte** bouton Nouveau.  
  
 **Cause**  
  
 Exécutez Internet Explorer avec le niveau de sécurité lorsque la valeur basse, requêtes Web sont exécutées avec de faibles privilèges. Pour répondre aux exigences de sécurité intégrée de Windows, Internet Explorer transmet un jeton d'utilisateur avec des privilèges minimaux.  
  
 Si vous utilisez Internet Explorer sur l'ordinateur sur lequel le portail BAM est installé et que vous définissez un niveau de sécurité faible dans Internet Explorer, le portail emprunte l'identité de l'utilisateur possédant le jeton associé à de faibles privilèges. Ce jeton n'accorde pas le droit d'écrire dans le journal des événements. Si le portail rencontre une erreur, il tente de la noter dans le journal des événements mais n'y parvient pas en raison des faibles privilèges du jeton d'utilisateur.  
  
 **Résolution**  
  
 Si vous voulez aller sur Internet à partir de l'ordinateur local, vous devez ajouter l'adresse http://localhost à la liste des sites de confiance.  
  
#### <a name="add-localhost-to-the-list-of-trusted-sites"></a>Ajouter localhost à la liste des sites de confiance  
  
1.  Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.  
  
2.  Cliquez sur le **sécurité** onglet, puis cliquez sur **Sites de confiance** dans les **sélectionner une zone pour afficher ou modifier les paramètres de sécurité** fenêtre.  
  
3.  Cliquez sur le **Sites** bouton.  
  
4.  Dans le **ajouter ce site Web à la zone** zone de texte, tapez **http://localhost**. Si le **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher est activée, désactivez-la, puis cliquez sur le **ajouter** bouton. Le site, le http://localhost, apparaît dans le **sites Web** liste.  
  
5.  Si nécessaire, restaurez la **exiger un serveur sécurisé (https :) pour tous les sites dans cette zone** case à cocher à son état d’origine.  
  
6.  Cliquez sur le **fermer** bouton, puis cliquez sur **OK**.  
  
## <a name="bam-portal-aggregations-do-not-populate-existing-data-when-using-an-ip-address-as-a-url-in-internet-explorer"></a>Agrégations du portail BAM ne remplissent pas les données existantes lors de l’utilisation d’une adresse IP en tant qu’URL dans Internet Explorer
 **Problème**  
  
 Lorsque vous utilisez une adresse IP en tant qu’URL avec Internet Explorer pour afficher le portail BAM, les agrégations affichent le message suivant : « aucun détail. La requête n'a pas pu être traitée. »  
  
 **Cause**  
  
 Les paramètres de sécurité par défaut dans Internet Explorer peuvent empêcher l’accès à des sites à l’aide des adresses IPv4 et IPv6 en tant qu’URL.  
  
 **Résolution**  
  
 Ajoutez l'adresse du site à la liste des sites de confiance et activez l'accès aux sources de données sur les domaines.  
  
#### <a name="add-the-ip-address-to-the-trusted-sites-list"></a>Ajouter l’adresse IP à la liste des sites de confiance  
  
1.  Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.  
  
2.  Cliquez sur le **sécurité** onglet, puis cliquez sur le **sites de confiance** zone de sécurité.  
  
3.  Cliquez sur le **Sites** bouton.  
  
4.  Dans **ajouter ce site Web à la zone**, tapez l’adresse IP du portail BAM, puis cliquez sur **ajouter**.  
  
5.  Cliquez sur **Fermer**, puis sur **OK**.  
  
#### <a name="enable-access-to-data-sources-across-domains"></a>Activer l’accès aux sources de données sur plusieurs domaines  
  
1.  Dans Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.  
  
2.  Cliquez sur le **sécurité** onglet, puis cliquez sur le **Sites de confiance** zone de sécurité.  
  
3.  Cliquez sur le **niveau personnalisé** bouton que vous faites défiler jusqu'à la **divers** nœud de la **paramètres** arborescence.  
  
4.  Dans le **accéder aux sources de données sur plusieurs domaines** nœud, cliquez sur le **activer la case d’option** bouton, puis cliquez sur **OK**.  
  
## <a name="bmexe-does-not-run-in-powershell"></a>BM.exe ne s'exécute pas dans PowerShell  
 **Problème**  
  
 La commande suivante génère une erreur lors de son exécution dans PowerShell.  
  
```  
bm.exe get-config -FileName:config.xml  
```  
  
 **Cause**  
  
 PowerShell n'a pas pu localiser le chemin d'accès des fichiers .exe et config.  
  
 **Résolution**  
  
 Si vous utilisez bm.exe dans PowerShell, spécifiez le chemin d'accès complet des fichiers .exe et config. Par exemple : `bm.exe get-config -FileName:config.xml` doit être spécifié en tant que `“%BizTalkPathTracking%”\bm.exe get-config -FileName:”%InstallDir%”\Tracking\config.xml`.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification du portail BAM](../core/planning-for-the-bam-portal.md)
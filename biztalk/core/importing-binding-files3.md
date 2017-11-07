---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 5c5cce40f3fbeb580ec7ba854d02cb243e1742b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="importing-binding-files"></a>importation des fichiers de liaison

## <a name="overview"></a>Vue d'ensemble
Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards. Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme *****. 
  
> [!NOTE]
>  Déploiement remplace la configuration de l’emplacement de réception. Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.  
  
## <a name="import-the-binding-files"></a>Importer les fichiers de liaison  
  
1.  Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.  
  
2.  Développez successivement Administration de BizTalk Server, **groupe BizTalk**, puis développez **Applications**.  
  
3.  Cliquez sur l’application souhaitée, pointez sur **importation**, puis cliquez sur **liaisons**.  
  
4.  Dans le **importer les liaisons** boîte de dialogue Parcourir et sélectionner les fichiers de liaison, puis cliquez sur **ouvrir**.  
  
## <a name="cleaning-the-target-computer"></a>Nettoyage de l'ordinateur cible  
Supprimez les ports d’envoi et les emplacements de réception qui sont liés à l’orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter les artefacts à l’Administration de BizTalk](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Importer le JD Edwards OneWorld application](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)
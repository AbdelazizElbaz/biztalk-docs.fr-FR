---
title: "Observations à caractère international pour la conception d’Applications BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9daaaaf7-6149-4e62-9e9b-b6356fc820d2
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef22467c18580219e8587d63017d8bf146090d4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="international-considerations-for-designing-biztalk-applications"></a>Observations à caractère international pour la conception d’Applications BizTalk
Nous vous recommandons vivement d'analyser les problèmes connus suivants lorsque vous développez vos applications [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] internationales.  
  
 **Restrictions de caractères pour les noms d’ordinateur**  
  
 L’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur les ordinateurs avec des noms qui contiennent des lettres en dehors de l’ensemble suivant n’est pas pris en charge : des lettres (A-Z, a-z), chiffres (0-9), des traits d’union (-) et des traits de soulignement (_). Seuls les noms d'ordinateur composés de ces caractères sont pris en charge.  
  
 **Caractères ne s’affichent pas correctement ou n’apparaissent pas du tout en raison d’une police incorrecte et les paramètres de secours de police**  
  
 Vous pouvez rencontrer des problèmes d'affichage des caractères (avec les caractères tchèques par exemple) dans les outils [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hébergés dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour y remédier, il peut s'avérer nécessaire de modifier les paramètres de polices disponibles dans l'onglet Options de Visual Studio et de sélectionner une autre police prenant en charge ces caractères. Vous pouvez sélectionner Tahoma ou Microsoft Sans Serif comme police par défaut pour lesquelles des fonctionnalités de police de substitution sont fournies.  
  
 **Caractères de paire de substitution affichent sous forme de carrés dans la console d’Administration de BizTalk Server et l’autre serveur BizTalk outils**  
  
 Les caractères de paire de substitution peuvent ne pas s'afficher dans la console Administration et d'autres outils [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les paires de substitution sont une représentation de caractère codée pour un seul caractère abstrait, consistant en une suite de deux unités de code. Vérifiez que la police installée sur votre système est appropriée (elle est incluse dans les versions chinoises de Office XP et 2003). Il peut également s'avérer nécessaire de modifier les options de police des outils disposant de cette fonctionnalité (tels que [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]).  
  
 Dans d'autres outils ne disposant pas d'option de configuration de police, les caractères de paire de substitution s'affichent sous forme de carrés, comme dans la console Administration par exemple. Si vous voyez des carrés, les caractères ne sont pas endommagées ; ils simplement ne peut pas être affichés correctement en raison d’un manque de prise en charge de la police.  
  
 **Restrictions de caractères de Services Web**  
  
 Si vous prévoyez de publier une orchestration en tant que service Web, vous pouvez rencontrer des problèmes avec les caractères utilisés dans les noms d'orchestration et de port, car ceux-ci sont utilisés dans les noms de fichier de services Web (fichiers .asmx) et le répertoire virtuel de l'Assistant Publication de services Web. Seul Microsoft Internet Information Services (IIS) 7.0 (inclus dans Microsoft Windows Server 2008 et Windows Vista) prend totalement en charge les caractères Unicode. Par conséquent, si vous utilisez une version antérieure de IIS ou Windows, les noms des orchestrations, ports, services Web et répertoires virtuels doivent uniquement inclure des caractères ANSI pris en charge par la version linguistique de Windows (par exemple, les caractères japonais ne sont pas autorisés dans la version anglaise de Windows).  
  
 Notez également que les noms de projet associés aux services Web dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sont restreints aux caractères ASCII.  
  
 **Utilisation des différents codages de document**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge un grand nombre de codages différents pour les documents de fichier plat et XML, par exemple UTF-16, UTF-8, chinois simplifié GBK, chinois simplifié GB18030, etc.  
  
 Pour les documents entrants, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reconnaît la déclaration de codage dans les documents XML, tel que «\<? xml version = « 1.0 » encoding = « GB2312 » ?\>». Le schéma de fichier plat possède un **Page de codes** propriété pour indiquer le codage des documents de fichier plat entrant.  
  
 Pour les documents sortants, XML et les assembleurs de fichier plat, utilisez le **jeu de caractères cible** propriété. Si cette propriété est spécifiée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] convertit les documents sortants dans le jeu de caractères spécifié sans tenir compte du jeu d'origine. Si aucun **jeu de caractères cible** propriété est définie, XML utilise le protocole UTF-8 et fichiers plats utilisent la page de codes spécifiée dans le schéma de fichier plat.  
  
 **Conversion de code à partir d’une page de codes non prise en charge pour une page de codes Windows**  
  
 Pour implémenter des conversions de code d'une page de codes non prise en charge en une page de codes Windows, vous devez créer un composant de pipeline personnalisé.  
  
 **Impact des marques d’ordre d’octet avec codage de document**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détermine le codage des caractères et génère, de manière différente pour les messages de fichier plat et XML, des documents dotés d'un codage particulier.  
  
 **Éditeur de schéma peut contenir des propriétés dans plusieurs langues**  
  
 Les noms de propriété XSD (XML Schema Definition language) affichés dans la fenêtre des propriétés de l'Éditeur de schéma et dans le code source XML ne sont pas localisés, et sont en anglais dans toutes les versions localisées. Les autres propriétés apparaissent dans la langue locale. Par exemple, dans la version en chinois simplifié de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les propriétés de schéma sont en anglais, mais les autres s'affichent en chinois.  
  
 **Données dépendant des paramètres régionaux dans les fichiers plats**  
  
 De nombreux paramètres régionaux représentent les données (par exemple, date, heure, nombre et devise) à l'aide de formats différents de ceux définis dans la norme XML. Par exemple, plusieurs paramètres régionaux utilisent un séparateur décimal autre que le point (.), et donc le nombre cinq et trois quarts peut être représenté par 5,75.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], tous les champs provenant des fichiers plats, à l'exception de ceux de date et d'heure, sont traités comme des chaînes afin que l'analyse puisse réussir. Cependant, lorsque vous utilisez la validation XML, le message XML résultant échoue lors de la validation par rapport au schéma.  
  
 Pour les champs de date et d'heure, l'analyseur tente d'analyser la valeur de champ de l'instance DateTime à l'aide d'un format de date ou d'heure personnalisé s'il est défini et l'écrit au format XML, ou utilise la valeur d'origine comme chaîne si le format n'est pas défini. En outre, si vous utilisez la validation XML, la validation de la date ou de l'heure résultante peut échouer si un format personnalisé n'est pas utilisé et que la valeur de champ utilisée dans le message de fichier plat n'était pas au format XML correct.  
  
 Notez que vous pouvez également créer des mappages ou des composants de pipeline personnalisés afin de mettre à jour les valeurs de champ et générer un XML valide.  
  
 **Prise en charge de langage de définition BAM**  
  
 Avant de déployer un fichier XML de définition BAM, vous devez vous assurer que la langue utilisée pour le créer correspond aux paramètres régionaux de l'ordinateur sur lequel vous le déployez. Si les paramètres du fichier et de l'ordinateur ne correspondent pas, vous devez d'abord redémarrer l'ordinateur utilisé pour exécuter BM.exe.  
  
> [!NOTE]
>  Le fichier XML de définition BAM ne peut pas contenir de texte en plusieurs langues à moins qu'elles utilisent le même codepage, ou que seules deux langues soient utilisées, dont l'anglais.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’encodage de caractères dans un composant de Pipeline](../core/implementing-character-encoding-in-a-pipeline-component.md)   
 [Gestion du codage dans un composant de Pipeline désassembleur](../core/handling-encoding-in-a-disassembler-pipeline-component.md)   
 [Encodage de caractères dans le composant de Pipeline de désassembleur de fichier plat](../core/character-encoding-in-the-flat-file-disassembler-pipeline-component.md)   
 [Encodage de caractères dans le composant de Pipeline d’assembleur de fichier plat](../core/character-encoding-in-the-flat-file-assembler-pipeline-component.md)   
 [Encodage de caractères dans le composant de Pipeline assembleur XML](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)   
 [Codage des caractères dans le composant de pipeline Désassembleur XML](../core/character-encoding-in-xml-disassembler-pipeline-component.md)
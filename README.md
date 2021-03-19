# The Social-Engineer Toolkit (SET)

## Introduction

Selon la propre description donnée par [TrustedSec, LLC](https://www.trustedsec.com), la société de consulting américaine responsable du développement de ce produit, le [Social-Engineer Toolkit](https://github.com/trustedsec/social-engineer-toolkit/) est un framework de test d'intrusion open-source conçu pour l'ingénierie sociale. Le SET dispose d'un certain nombre de vecteurs d'attaque personnalisés qui vous permettent de réaliser rapidement une attaque crédible.

Le SET est spécifiquement conçu pour réaliser des attaques avancées contre l'élément humain. Il est rapidement devenu un outil standard dans l'arsenal des testeurs de pénétration. Les attaques intégrées dans la boîte à outils sont conçues pour être des attaques ciblées contre une personne ou une organisation utilisées lors d'un test de pénétration.


## Téléchargement et installation

Le SET est nativement supporté sur Linux et sur Mac OS X (experimental). Il est préinstallé sur Kali Linux et il est capable de se mettre à jour lui-même.

Pour une installation sur Ubuntu/Debian/Mac OS X :

```
git clone https://github.com/trustedsec/social-engineer-toolkit/ setoolkit/
cd setoolkit
pip3 install -r requirements.txt
python setup.py
```

## Que faut-il faire ?

Voici les activités à réalise dans ce laboratoire. Vous devez : 

- Installer le Social Engineering Toolkit (SET)
- Créer un collecteur d'identifiants (credential harvester)
- Capturer certains identifiants utilisateur (les vôtres)
- Créer une attaque de phishing
- Relier le collecteur d'identifiants à l'attaque

Le "rapport" de ce labo est très simple : **Pour chaque tâche, faites des captures d'écran de vos activités**.

## Note sur l'éthique

Il n'est absolument pas acceptable d'attaquer quelqu'un pour quelque raison que ce soit. 

L'utilisation de cet outil à des fins autres que votre propre éducation et formation sans autorisation est strictement interdite par les politiques de ce cours et de l'école, ainsi que par les lois. 

Le but de cet exercice est de vous permettre de vous familiariser avec les outils et comment ils peuvent être utilisés dans le contexte professionnel d'un pentest. Ça vous permettra aussi de comprendre les tactiques de l'adversaire afin de pouvoir les contrer par le biais de la politique, de l'éducation et de la formation.

## Execution de SET

Pour exécuter SET, dans votre terminal taper :

```
setoolkit
```

Dépendant de votre OS et de votre installation particulière, il est possible que certaines fonctionnalités ne soient pas disponibles au moins d'utiliser ```sudo```.

```
sudo setoolkit
```

# Exercice 1 - Credential Harvesting

Vous découvrirez l'un des outils les plus couramment utilisés par les ingénieurs sociaux et les acteurs malveillants pour tromper les cibles.

### Soumettre des captures d'écran

Pour le collecteur d'identifiants, montrez que vous avez cloné un site en indiquant son adresse web et l'interface d'utilisateur. Saisissez les informations d'identification sur votre clone local, puis cliquez le bouton de connexion. Essayez plusieurs sites comme facebook.com, twitter.com, et d'autres qui puissent vous intéresser. Faites des captures d'écran des mots de passe collectés dans vos tests avec SET.



### <u>Travail pratique</u>

1. Lancer SET `sudo setoolkit`
2. Sélectionner `1) Social-Engineering Attacks` > `2) Website Attack Vectors` > `3) Credential Harvester Attack Method`
3. Puis, sélectionner `2) Site Cloner`
4. Continuer en laissant l'adresse IP par défaut
5. Entrer l'URL du site à cloner : `https://gaps.heig-vd.ch/consultation/`
6. Accéder au site cloné sur `http://localhost/`



Voici le résultat ci-dessous. On peut noter que les caractère avec accent n'ont pas été cloné correctement.

![](images/gaps1.png)

Lorsque la victime entre ces identifiants de connexion, l'attaquant reçoit ces informations en claire :

![](images/gaps2.png)



Même résultat avec Twitter en utilisant un template fournit par SET cette fois :

![](images/twitter1.png)

![](images/twitter2.png)



Néanmoins, avec un processus de login plus complexe comme google par exemple, il n'est pas possible de récupérer le mot de passe car ce dernier est demandé sur une page différente.

![](images/google1.png)

Voici ce que le formulaire ci-dessus envoie comme paramètre. Le nom d'utilisateur se trouve à la 3ème ligne du screenshot. 

![](images/google2.png)

# Exercice 2 - Créer une attaque de phishing

Essayez la fonction d'attaque par phishing. C'est très facile à faire. Vous pouvez vous référer à ce lien pour plus d'informations http://www.computerweekly.com/tutorial/Social-Engineer-Toolkit-SET-tutorial-for-penetration-testers


# Exercice 3 - Explorer les liens "Phishy" et le courrier électronique "Phishy"

Pour cette dernière partie de notre exploration du phishing, nous allons utiliser un contenu réalisé par les  Dr. Matthew L. Hale, le Dr. Robin Gandhi et la Dr. Briana B. Morrison de [Nebraska GenCyber](
http://www.nebraskagencyber.com). 

Visitez : https://mlhale.github.io/nebraska-gencyber-modules/phishing/README/ et passez en revue les modules :

- Analyse d'url. **Ce module risque d'être beaucoup trop simple pour vous** mais il peut être très intéressant pour vos rapports de pentest, surtout comme outil pour sensibiliser les employés d'une entreprise. Gardez-le précieusement comme une partie de votre toolbox pour l'avenir.
- Analyse d'Email (ce module est probablement plus intéressant techniquement pour vous)

En général, c'est un bon exemple de matériel de formation et d'éducation qui peut aider à lutter contre les attaques de phishing et à sensibiliser le personnel d'une organisation.

Vous avez la liberté de reproduire et d'utiliser ce matériel grâce à sa licence.


### Soumettre des captures d'écran

Pour cette tâche, prenez des captures d'écran de :

- Vos inspections d'un en-tête de courrier électronique à partir de votre propre boîte de réception

### <u>Travail pratique</u>

Voici un e-mail que j'ai reçu sur ma boîte HEIG-VD et qui concerne des comptes microsoft.net (Analyse en bas) :

```
Received: from EIMAIL02.einet.ad.eivd.ch (10.192.41.72) by
 EIMAIL01.einet.ad.eivd.ch (10.192.41.71) with Microsoft SMTP Server
 (version=TLS1_2, cipher=TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256) id 15.1.2176.2
 via Mailbox Transport; Thu, 18 Mar 2021 07:22:29 +0100
Received: from EIMAIL02.einet.ad.eivd.ch (10.192.41.72) by
 EIMAIL02.einet.ad.eivd.ch (10.192.41.72) with Microsoft SMTP Server
 (version=TLS1_2, cipher=TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256) id
 15.1.2176.2; Thu, 18 Mar 2021 07:22:28 +0100
Received: from mail01.heig-vd.ch (10.192.222.28) by EIMAIL02.einet.ad.eivd.ch
 (10.192.41.72) with Microsoft SMTP Server (version=TLS1_2,
 cipher=TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256) id 15.1.2176.2 via Frontend
 Transport; Thu, 18 Mar 2021 07:22:28 +0100
X-ASG-Debug-ID: 1616048548-1114bd1d24972f60001-qbKJvj
Received: from nemx1a.ne.ch (nemx1a.ne.ch [148.196.30.42]) by mail01.heig-vd.ch with ESMTP id kqhTtKQQ8yFrt1cK (version=TLSv1.2 cipher=ECDHE-RSA-AES256-GCM-SHA384 bits=256 verify=NO); Thu, 18 Mar 2021 07:22:28 +0100 (CET)
X-Barracuda-Envelope-From: MehmetajEli@rpn.ch
X-Barracuda-Effective-Source-IP: nemx1a.ne.ch[148.196.30.42]
X-Barracuda-Apparent-Source-IP: 148.196.30.42
Received: from rpnedge1.rpn.ch ([157.26.1.37])
	by nemx1.ne.ch with esmtps (TLSv1.2:AES128-GCM-SHA256:128)
	(Exim 4.92)
	(envelope-from <MehmetajEli@rpn.ch>)
	id 1lMm34-0002Fu-TX; Thu, 18 Mar 2021 07:22:24 +0100
Received: from rpn3cmbx1.rpn.ch (157.26.0.55) by RPNEDGE1.rpn.ch (157.26.1.37)
 with Microsoft SMTP Server (version=TLS1_2,
 cipher=TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256) id 15.1.2176.2; Thu, 18 Mar
 2021 07:22:21 +0100
Received: from rpncmbx1.rpn.ch (157.26.0.35) by rpn3cmbx1.rpn.ch (157.26.0.55)
 with Microsoft SMTP Server (version=TLS1_2,
 cipher=TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256_P256) id 15.1.2176.2; Thu, 18
 Mar 2021 07:22:21 +0100
Received: from rpncmbx1.rpn.ch ([10.26.1.35]) by rpncmbx1.rpn.ch
 ([10.26.1.35]) with mapi id 15.01.2176.009; Thu, 18 Mar 2021 07:22:21 +0100
From: Mehmetaj Eliott <MehmetajEli@rpn.ch>
To: "Notice@microsoft.net" <Notice@microsoft.net>
Subject: Microsoft Account Team
Thread-Topic: Microsoft Account Team
X-ASG-Orig-Subj: Microsoft Account Team
Thread-Index: AdcbuuzOvfgs0InuQ4WwOkt1fhaPkAAABhSQAAAAY0AAAAA4gAAAADUQAAAALQAAAACfUAAAADWQAADDCiAAAAAfkAAAAC1QAAAAQXAAAAAXIAAAABsgAAAAGrAAAAAacAAAABygAAAAHqAAAAAckAAAABsgAAAAHoAAAAAgsAAAAB5wAAAAHmAAAAAgwAAAAB6AAAAAH+AAAAAgQAAAAB+gAAAAIGAAAAAhIAAAACOwAAAAIuAAAAAjoAAAACOQAAAAJVAAAAAl4AAAACQQAAAAJgAAAAAnwAAAACaAAAAAKBAAAAAo0AAAAChgAAAAKiAAAAAosA==
Date: Thu, 18 Mar 2021 06:22:21 +0000
Message-ID: <bac1e9ae6c4745c38bc21f28d4a13f74@rpn.ch>
Accept-Language: fr-FR, fr-CH, en-US
Content-Language: en-US
X-MS-Has-Attach:
X-MS-TNEF-Correlator:
x-originating-ip: [157.26.1.46]
Content-Type: multipart/alternative;
	boundary="_000_bac1e9ae6c4745c38bc21f28d4a13f74rpnch_"
MIME-Version: 1.0
X-Originating-IP: 157.26.1.37
X-EtatdeNeuchatel-Domain: rpn.ch
X-EtatdeNeuchatel-Username: 157.26.1.37
Authentication-Results: ne.ch; auth=pass smtp.auth=157.26.1.37@rpn.ch
X-EtatdeNeuchatel-Outgoing-Class: ham
X-EtatdeNeuchatel-Outgoing-Evidence: Combined (0.50)
X-Recommended-Action: accept
X-Report-Abuse-To: spam@nemx1.ne.ch
X-Barracuda-Connect: nemx1a.ne.ch[148.196.30.42]
X-Barracuda-Start-Time: 1616048548
X-Barracuda-Encrypted: ECDHE-RSA-AES256-GCM-SHA384
X-Barracuda-URL: https://quarantine.heig-vd.ch:443/cgi-mod/mark.cgi
X-Virus-Scanned: by bsmtpd at heig-vd.ch
X-Barracuda-Scan-Msg-Size: 3218
X-Barracuda-BRTS-Status: 1
X-Barracuda-Spam-Score: 0.20
X-Barracuda-Spam-Status: No, SCORE=0.20 using global scores of TAG_LEVEL=1000.0 QUARANTINE_LEVEL=4.0 KILL_LEVEL=5.0 tests=BSF_SC0_SA983, HTML_MESSAGE
X-Barracuda-Spam-Report: Code version 3.2, rules version 3.2.3.88604
	Rule breakdown below
	 pts rule name              description
	---- ---------------------- --------------------------------------------------
	0.00 HTML_MESSAGE           BODY: HTML included in message
	0.20 BSF_SC0_SA983          Custom Rule BSF_SC0_SA983
Return-Path: MehmetajEli@rpn.ch
X-MS-Exchange-Organization-Network-Message-Id: 2bfc3fcc-5fa7-4050-925e-08d8e9d634b8
X-MS-Exchange-Organization-AVStamp-Enterprise: 1.0
X-MS-Exchange-Organization-AuthSource: EIMAIL02.einet.ad.eivd.ch
X-MS-Exchange-Organization-AuthAs: Anonymous
X-MS-Exchange-Transport-EndToEndLatency: 00:00:00.1742262
X-MS-Exchange-Processed-By-BccFoldering: 15.01.2176.009
```

L'e-mail semble venir de `rpn.ch`. La première adresse IP associé (`157.26.0.35`) semble valide et est attribué au *Service informatique de l'Entite neuchateloise*.

Le `Return-Path:` indique la même adresse que l’expéditeur ce qui pourrait indique que ce n'est pas du spam.

Le système de filtrage de l'HEIG-VD indique un spam-score de 0.2 (`X-Barracuda-Spam-Score: 0.20`) ce qui semble être bas.

En analysant l'en-tête, cet e-mail ne semble pas être du spam. Néanmoins, le contenu de ce dernier contient principalement un lien dirigent vers un site douteux tout en indiquant que si on ne valide pas son compte avec le lien, notre compte Teams sera désactivé. Cela laisse pensé que c'est bien un e-mail malveillant.
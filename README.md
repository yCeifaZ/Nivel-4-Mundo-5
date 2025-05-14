<!-- PROJECT LOGO -->
<div align="center">
   <a href="https://github.com/othneildrew/Best-README-Template">
      <img src="https://logodownload.org/wp-content/uploads/2014/12/estacio-logo-1-2048x1641.png" alt="estacio logo" width="80"                  height="80">
   </a>
    <h1 align="center"> Universidade Estácio de Sá </h1>
     <hr>
</div> 

* DESENVOLVIMENTO FULL STACK- 
* Disciplina: RPG0034  - Dando inteligência ao software
* Semestre Letivo: 2025.1
* Repositorio Git: https://github.com/yCeifaZ/Nivel-4-Mundo-5.git

<hr>

* [LUCIANO BENTO DE SOUSA FILHO] - MATRICULA: 202302068766
<hr>
 <h1 align="center"> Missão Prática | Nível 4 | Mundo 5 </h1>
 <h2 align="left" > Dando inteligência ao software </h2> 
 <hr>
 
 <h2> :clipboard: Objetivos da Prática </h2>

* Configurar o ambiente Google Colab;
* Descrever tarefas diversas relacionadas ao Processamento de Linguagem Natural;
* Descrever o processo de identificação de entidades a partir de textos;
* Descrever o processo de extração de frases-chave a partir de textos;
* Descrever o processo de identificação de linguagem predominante a partir de textos;

<hr>
<h2> Contextualização </h2>

Recentemente a empresa em que você trabalha, como Analista de Data Science,
foi contratada por uma grande empresa interessada em abrir, no Brasil, centros
de treinamento esportivos vinculados a grandes clubes de futebol da Inglaterra.
Nesse contexto, a empresa contratante deseja saber a percepção das pessoas
em relação aos clubes citados, i.e., de uma forma geral, qual o sentimento delas,
expressos através de textos publicados em redes sociais, sobre os mesmos.

Para essa atividade você deverá aplicar a Analise de Sentimentos, tarefa de
Processamento de Linguagem Natural com uso de Machine Learning. Todo o
passo-a-passo necessário para a atividade é descrito a seguir.
<hr>
<h2> Códigos </h2>

# As atividades foram desenvolvidas no Google Colab.
https://github.com/yCeifaZ/Nivel-4-Mundo-5/blob/main/sentiment.ipynb

``` Python

Análise de Sentimentos

#Passo 1: Instalando as bibliotecas e recarregando o ambiente


!pip install -U pip setuptools wheel

!pip install -U spacy

!python -m spacy download en_core_web_sm

!pip install spacytextblob

import pkg_resources,imp

imp.reload(pkg_resources)


# Passo 2: Importando as bibliotecas para análise de sentimento


import spacy

from spacytextblob.spacytextblob import SpacyTextBlob


# Passo 3: Definindo o modelo e a pipeline a serem utilizadas na análise


nlp = spacy.load('en_core_web_sm')

nlp.add_pipe('spacytextblob')

Out:
<spacytextblob.spacytextblob.SpacyTextBlob at 0x7923722e20e0>


# Passo 4: Definindo o texto inicial a ser analisado para verificação/validação da biblioteca


user_input = 'This is a wonderful campsite. I loved the serenity and the birds chirping in the morning.'

doc = nlp(user_input)


# Passo 5: Exibindo o resultado da primeira análise (um range entre -1 [avaliação negativa] e 1 [avaliação positiva]


input_polarity = doc._.polarity

sentiment = {

    'score': input_polarity

}

print(sentiment)

Out:
{'score': 0.85}

# Passo 6: Definindo a lista de tweets a serem analisadas

tweets=["Bayer Leverkusen goalkeeper Bernd Leno will not be going to Napoli. His agent Uli Ferber to Bild: I can confirm that there were negotiations with Napoli, which we have broken off. Napoli is not an option. Atletico Madrid and Arsenal are the other strong rumours. #B04 #AFC",

"Gary Speed v Blackburn at St James in 2001/02 anyone? #NUFC #BEL #JAP#WorldCup",

"@ChelseaFC Don't make him regret it and start him over Hoofiz",

"@LiverpoolFF @AnfieldEdition He's a liar, made up. I've unfollowed him as loads of others have. Pure blagger. #LFC",

"@theesk @Everton Didn't realise Kenwright is due to leave at the end of the month. In all seriousness could you see him being interested in us?",

"@hasanshahbaz19 @LFC My knowledge has decreased somewhat in the past few seasons",

"Report: Linked with #Everton and #Wolves, Italians set to sign £4.5m-rated winger",

"Am seeing tweets that there’s been a fall out @Everton between the money men... I’m presuming it’s just a quiet news day or some kopite with nothing better to do! @ALANMYERSMEDIA",

"@LFC @officialAL20 @IntChampionsCup @ManUtd Expect loads of excuses after tonight’s game",

"@MartinDiamond17 @azryahmad @Baren_D @Mathewlewis1997 @iamheinthu @DiMarzio @Alissonbecker @LFC @SkySportsNews @SkySport @OfficialASRoma I’m just fine I have your fanbase angry over stating facts should ask them hun. Xo",

"What a weekend of football results! @ManUtd @Glentoran @RangersFC &amp; Hearts ????",

"@ChelseaFC For the first time in a long while, my heart was relaxed while watching Chelsea. Really enjoyed it today. Come on, CHELSEA!!!",

"@ChelseaFC @CesarAzpi What a fantastic signing worth every single penny ??",

"Pogba scores, Pogba assists. But tomorrow papers won't be telling you this, instead they will tell you how he'll end up at Juve because he's unhappy, frustrated, have grudges with Mourinho and so on and so forth #mufc",

"@WestHamUtd we need to keep @CH14_ and get @HirvingLozano70 to compliment",

"@kevdev9 @Everton Shouldn’t be happening! Needs to stay away with his venomous attitude until he is sold!",

"@brfootball @aguerosergiokun @ManCity What a genius. Pep taking winning mentality with him, conquering league after league. Baller",

"@HMZ0709  Can we get a RT for our #lfc Mo Salah Liverpool Enamel Pin Badge"]


# Passo 7: Analisando os tweets

for item in tweets:

  doc = nlp(item)

  input_polarity = doc._.polarity

  sentiment = {

      'tweet': item,

      'score': input_polarity

  }

  print(sentiment)

Out:

{'tweet': 'Bayer Leverkusen goalkeeper Bernd Leno will not be going to Napoli. His agent Uli Ferber to Bild: I can confirm that there were negotiations with Napoli, which we have broken off. Napoli is not an option. Atletico Madrid and Arsenal are the other strong rumours. #B04 #AFC', 'score': -0.030555555555555575}
{'tweet': 'Gary Speed v Blackburn at St James in 2001/02 anyone? #NUFC #BEL #JAP#WorldCup', 'score': 0.0}
{'tweet': "@ChelseaFC Don't make him regret it and start him over Hoofiz", 'score': 0.0}
{'tweet': "@LiverpoolFF @AnfieldEdition He's a liar, made up. I've unfollowed him as loads of others have. Pure blagger. #LFC", 'score': 0.21428571428571427}
{'tweet': "@theesk @Everton Didn't realise Kenwright is due to leave at the end of the month. In all seriousness could you see him being interested in us?", 'score': 0.0625}
{'tweet': '@hasanshahbaz19 @LFC My knowledge has decreased somewhat in the past few seasons', 'score': -0.2833333333333334}
{'tweet': 'Report: Linked with #Everton and #Wolves, Italians set to sign £4.5m-rated winger', 'score': 0.0}
{'tweet': 'Am seeing tweets that there’s been a fall out @Everton between the money men... I’m presuming it’s just a quiet news day or some kopite with nothing better to do! @ALANMYERSMEDIA', 'score': 0.3125}
{'tweet': '@LFC @officialAL20 @IntChampionsCup @ManUtd Expect loads of excuses after tonight’s game', 'score': -0.4}
{'tweet': '@MartinDiamond17 @azryahmad @Baren_D @Mathewlewis1997 @iamheinthu @DiMarzio @Alissonbecker @LFC @SkySportsNews @SkySport @OfficialASRoma I’m just fine I have your fanbase angry over stating facts should ask them hun. Xo', 'score': -0.04166666666666666}
{'tweet': 'What a weekend of football results! @ManUtd @Glentoran @RangersFC &amp; Hearts ????', 'score': 0.0}
{'tweet': '@ChelseaFC For the first time in a long while, my heart was relaxed while watching Chelsea. Really enjoyed it today. Come on, CHELSEA!!!', 'score': 0.39218749999999997}
{'tweet': '@ChelseaFC @CesarAzpi What a fantastic signing worth every single penny ??', 'score': 0.20952380952380953}
{'tweet': "Pogba scores, Pogba assists. But tomorrow papers won't be telling you this, instead they will tell you how he'll end up at Juve because he's unhappy, frustrated, have grudges with Mourinho and so on and so forth #mufc", 'score': -0.6499999999999999}
{'tweet': '@WestHamUtd we need to keep @CH14_ and get @HirvingLozano70 to compliment', 'score': 0.0}
{'tweet': '@kevdev9 @Everton Shouldn’t be happening! Needs to stay away with his venomous attitude until he is sold!', 'score': 0.0}
{'tweet': '@brfootball @aguerosergiokun @ManCity What a genius. Pep taking winning mentality with him, conquering league after league. Baller', 'score': 0.5}
{'tweet': '@HMZ0709  Can we get a RT for our #lfc Mo Salah Liverpool Enamel Pin Badge', 'score': 0.0}

```

<H3>NAME: Sai Darshan G</H3>
<H3>REGISTER NO : 212221240047</H3>
<H3>EX. NO.6</H3>
<H3>DATE:</H3>
<H1 ALIGN =CENTER>Implementation of Semantic Analysis</H1>
<H3>Aim: 
 
 To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1: Import the nltk library.<br>
Step 2: Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.<br>
Step 3:Accept user input for the text.<br>
Step 4:Tokenize the input text into words using the word_tokenize function.<br>
Step 5:Iterate through each word in the tokenized text.<br>
•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.<br>
•	Print each word along with its corresponding part-of-speech tag.<br>
•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).<br>
•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.<br>
•	Print the unique sets of synonyms and antonyms.


## PROGRAM
```
import nltk
from nltk.corpus import wordnet
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
nltk.download('punkt')
def get_verbs(sentence):
    verbs = []
    pos_tags = nltk.pos_tag(nltk.word_tokenize(sentence))
    for word, tag in pos_tags:
        if tag.startswith('V'):  # Verbs start with 'V' in the POS tag
            verbs.append(word)
    return verbs
def get_synonyms(word):
    synonyms = []
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.append(lemma.name())
    return synonyms
def read_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text
def main():
    file_path = 'sample.txt'
    text = read_text_file(file_path)
    sentences = nltk.sent_tokenize(text)
    all_verbs = []
    synonyms_dict = {}
    for sentence in sentences:
        verbs = get_verbs(sentence)
        all_verbs.extend(verbs)
        for verb in verbs:
            synonyms = get_synonyms(verb)
            synonyms_dict[verb] = synonyms
    with open('output.csv', 'w', newline='') as csvfile:
        writer = csv.writer(csvfile)
        writer.writerow(['Verb', 'Synonyms'])
        for verb, synonyms in synonyms_dict.items():
            writer.writerow([verb, ', '.join(synonyms)])

if __name__ == '__main__':
    main()
```
## OUTPUT
|Verb|Synonyms|
|---|---|
|was|Washington, Evergreen\_State, WA, be, be, be, exist, be, be, equal, be, constitute, represent, make\_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be|
|named|name, call, name, identify, name, nominate, make, appoint, name, nominate, constitute, name, mention, advert, bring\_up, cite, name, refer, identify, discover, key, key\_out, distinguish, describe, name, list, name, diagnose, name|
|lived|populate, dwell, live, inhabit, live, survive, last, live, live\_on, go, endure, hold\_up, hold\_out, exist, survive, live, subsist, be, live, know, experience, live, live|
|loved|love, love, enjoy, love, sleep\_together, roll\_in\_the\_hay, love, make\_out, make\_love, sleep\_with, get\_laid, have\_sex, know, do\_it, be\_intimate, have\_intercourse, have\_it\_away, have\_it\_off, screw, fuck, jazz, eff, hump, lie\_with, bed, have\_a\_go\_at\_it, bang, get\_it\_on, bonk, loved|
|explore|research, search, explore, explore, explore, explore|
|exploring|research, search, explore, explore, explore, explore|
|came|come, come\_up, arrive, get, come, come, come, come, follow, come, issue\_forth, come, hail, come, come, come, come, fall, come, come, total, number, add\_up, come, amount, come, add\_up, amount, come, come\_in, occur, come, derive, come, descend, do, fare, make\_out, come, get\_along, come, come|
|peered|peer|
|see|see, see, understand, realize, realise, see, witness, find, see, visualize, visualise, envision, project, fancy, see, figure, picture, image, see, consider, reckon, view, regard, learn, hear, get\_word, get\_wind, pick\_up, find\_out, get\_a\_line, discover, see, watch, view, see, catch, take\_in, meet, run\_into, encounter, run\_across, come\_across, see, determine, check, find\_out, see, ascertain, watch, learn, see, check, insure, see\_to\_it, ensure, control, ascertain, assure, see, see, visit, see, attend, take\_care, look, see, see, go\_steady, go\_out, date, see, see, see, see, examine, see, experience, see, go\_through, see, escort, see, interpret, construe, see|
|decided|decide, make\_up\_one's\_mind, determine, decide, settle, resolve, adjudicate, decide, decide, distinct, decided|
|climb|ascent, acclivity, rise, raise, climb, upgrade, climb, climbing, mounting, climb, mount, climb, climb\_up, mount, go\_up, climb, wax, mount, climb, rise, climb, climb, rise, go\_up, climb|
|led|light-emitting\_diode, LED, lead, take, direct, conduct, guide, leave, result, lead, lead, lead, head, lead, run, go, pass, lead, extend, head, lead, lead, top, contribute, lead, conduce, conduct, lead, direct, go, lead, precede, lead, run, lead, moderate, chair, lead|
|fell|hide, fell, fell, felled\_seam, fell, fell, drop, strike\_down, cut\_down, fly, fell, vanish, fell, fall, descend, fall, go\_down, come\_down, fall, fall, come, precipitate, come\_down, fall, fall, fall, fall, shine, strike, fall, fall, decrease, diminish, lessen, fall, fall, fall, fall, fall, fall, fall, fall, accrue, fall, fall, light, fall, return, pass, devolve, fall, fall, fall\_down, fall, hang, fall, flow, fall, fall, fall, fall, fall, fall, fall, descend, settle, barbarous, brutal, cruel, fell, roughshod, savage, vicious|
|landed|land, set\_down, land, put\_down, bring\_down, bring, land, land, land, land, set\_ashore, shore, down, shoot\_down, land, landed|
|found|found, establish, set\_up, found, launch, establish, found, plant, constitute, institute, establish, base, ground, found, find, happen, chance, bump, encounter, detect, observe, find, discover, notice, find, regain, determine, find, find\_out, ascertain, find, feel, witness, find, see, line\_up, get\_hold, come\_up, find, discover, find, discover, find, find, rule, find, receive, get, find, obtain, incur, find, recover, retrieve, find, regain, find, find\_oneself, find, found|
|were|be, be, be, exist, be, be, equal, be, constitute, represent, make\_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be|
|talking|talk, talking, talk, speak, talk, speak, utter, mouth, verbalize, verbalise, speak, talk, spill, talk, spill\_the\_beans, let\_the\_cat\_out\_of\_the\_bag, talk, tattle, blab, peach, babble, sing, babble\_out, blab\_out, lecture, talk|
|had|have, have\_got, hold, have, feature, experience, receive, have, get, own, have, possess, get, let, have, consume, ingest, take\_in, take, have, have, hold, throw, have, make, give, have, have, have, experience, have, induce, stimulate, cause, have, get, make, accept, take, have, receive, have, suffer, sustain, have, get, have, get, make, give\_birth, deliver, bear, birth, have, take, have|
|learned|learn, larn, acquire, learn, hear, get\_word, get\_wind, pick\_up, find\_out, get\_a\_line, discover, see, memorize, memorise, con, learn, learn, study, read, take, teach, learn, instruct, determine, check, find\_out, see, ascertain, watch, learn, erudite, learned, knowing, knowledgeable, learned, lettered, well-educated, well-read, conditioned, learned|
|arguing|controversy, contention, contestation, disputation, disceptation, tilt, argument, arguing, argue, reason, argue, contend, debate, fence, argue, indicate|
|do|bash, do, brawl, do, doh, ut, Doctor\_of\_Osteopathy, DO, make, do, perform, execute, do, do, perform, do, fare, make\_out, come, get\_along, cause, do, make, practice, practise, exercise, do, suffice, do, answer, serve, do, make, act, behave, do, serve, do, do, manage, dress, arrange, set, do, coif, coiffe, coiffure, do|
|terrorizing|terrorize, terrorise, terrify, terrorize, terrorise|
|help|aid, assist, assistance, help, assistant, helper, help, supporter, aid, assistance, help, avail, help, service, help, assist, aid, help, aid, help, facilitate, help\_oneself, help, serve, help, help, avail, help, help|
|defeat|defeat, licking, frustration, defeat, get\_the\_better\_of, overcome, defeat, kill, shoot\_down, defeat, vote\_down, vote\_out|
|went|travel, go, move, locomote, go, proceed, move, go, go\_away, depart, become, go, get, go, run, go, run, go, pass, lead, extend, proceed, go, go, go, sound, go, function, work, operate, go, run, run\_low, run\_short, go, move, go, run, survive, last, live, live\_on, go, endure, hold\_up, hold\_out, go, die, decease, perish, go, exit, pass\_away, expire, pass, kick\_the\_bucket, cash\_in\_one's\_chips, buy\_the\_farm, conk, give-up\_the\_ghost, drop\_dead, pop\_off, choke, croak, snuff\_it, belong, go, go, start, go, get\_going, move, go, go, go, blend, go, blend\_in, go, lead, fit, go, rifle, go, go, plump, go, fail, go\_bad, give\_way, die, give\_out, conk\_out, go, break, break\_down|
|challenged|challenge, dispute, gainsay, challenge, challenge, challenge, take\_exception|
|surprised|surprise, surprise, storm, surprise, surprised|
|agreed|agree, hold, concur, concord, agree, match, fit, correspond, check, jibe, gibe, tally, agree, harmonize, harmonise, consort, accord, concord, fit\_in, agree, agree, agree, agree, agreed, in\_agreement|
|fight|battle, conflict, fight, engagement, fight, fighting, combat, scrap, competitiveness, fight, fight, fight, contend, fight, struggle, fight, oppose, fight\_back, fight\_down, defend, fight, struggle, crusade, fight, press, campaign, push, agitate|
|fought|contend, fight, struggle, fight, oppose, fight\_back, fight\_down, defend, fight, struggle, crusade, fight, press, campaign, push, agitate|
|defeated|defeated, discomfited, get\_the\_better\_of, overcome, defeat, kill, shoot\_down, defeat, vote\_down, vote\_out, defeated, defeated, disappointed, discomfited, foiled, frustrated, thwarted|
|saving|economy, saving, rescue, deliverance, delivery, saving, preservation, saving, salvage, salve, relieve, save, save, preserve, save, carry\_through, pull\_through, bring\_through, save, save, lay\_aside, save\_up, save, make\_unnecessary, deliver, redeem, save, spare, save, save, economize, economise, keep\_open, hold\_open, keep, save, write, save, redemptive, redeeming, saving, saving|
|threw|throw, throw, shed, cast, cast\_off, shake\_off, throw, throw\_off, throw\_away, drop, throw, thrust, give, throw, throw, flip, switch, project, cast, contrive, throw, throw, bewilder, bemuse, discombobulate, throw, hurl, throw, hold, throw, have, make, give, throw, throw, throw, confuse, throw, fox, befuddle, fuddle, bedevil, confound, discombobulate|

## RESULT
Thus, we have successfully implemented a program for Natural Language Processing.

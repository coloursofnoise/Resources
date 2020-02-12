## Character Dialogue
Character Dialogue in Celeste is contained within the `Sfxs` bank, under the path `event:/char/dialogue/`.
Each dialogue has two parameters: 
- `dialogue_portrait`, which ranges from 0-12, and
- `dialogue_end`, 0-1, which applies a low-pass filter for a more muted sound.

For questions or feedback, contact @coloursofnoise on the Celeste Discord

## Characters:
- [**Madeline**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#madeline)  
- [**Theo**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#theo)  
- [**Badeline**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#badeline)  
- [**Granny**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#granny)  
- [**Oshiro**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#oshiro)  
- [**Others**](https://github.com/EverestAPI/Resources/wiki/Character-Dialogue#others)


## Madeline
path: `madeline` or `madeline_mirror`  
actual range: 1-11
1. normal
2. distracted
3. sad
4. deadpan
5. determined, determinedclosed
6. surprised
7. upset
8. angry
9. panic
10. sadder
11. peaceful


## Theo
path: `theo` or `theo_mirror`  
actual range: 1-8
1. excited
2. nailedit
3. normal
4. serious
5. thinking
6. worried
7. wtf
8. yolo

## Badeline
path: `badeline`  
actual range: 1-11
1. angry
2. freakA, freakB, freakC, freakC_cont, freakBAlt, freakCAlt
3. normal
4. sad
5. scoff
6. Serious, serious_alt
7. upset
8. Worried, worriedAlt
9. yell
10. concerned
11. angryAlt

## Granny 1-3
path: `granny`  
actual range: 1-3
1. normal
2. laugh
3. mock

## Oshiro
path: `oshiro`  
actual range: 1-9
1. drama
2. lostcontrol
3. nervous
4. normal
5. serious
6. sidehappy
7. sidesuspicious
8. sideworried
9. worried

## Others
### Mom 1-2
path: `mom`  
actual range: 1-2
1. normal
2. concerned

### Ex
path: `ex`  
1. normal

### Secret Character
path: `secret_character`  
The secret character does not have `dialogue_end` or `dialogue_portrait` parameters.

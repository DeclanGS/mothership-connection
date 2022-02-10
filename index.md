<html>
<body>

<button type="button" onclick="myFunction()">Generate New</button>

<p id="demo">Who's up?</p>

<script>
function myFunction() { 

(function(){
  "use strict";

function choice(thing){
    return thing[Math.floor(Math.random() * thing.length)];
}

function remove(arr, value) {
  var index = arr.indexOf(value);
  if (index > -1) {
    arr.splice(index, 1);
  }
  return arr;
}

var skills = ['Linguistics', 'Zoology', 'Botany', 'Geology', 'Industrial Equipment', 'Jury-Rigging', 'Chemistry',
          'Computers', 'Zero-G', 'Mathematics', 'Art', 'Archaeology', 'Theology', 'Military Training', 'Rimwise', 'Athletics']

var char = {charclass : choice(['Marine','Android','Scientist','Teamster'])}
             
char.strength = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 22
char.speed = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 22
char.intellect = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 22
char.combat = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 22

char.sanity = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 12
char.fear = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 12
char.body = Math.floor(Math.random() * 10) + Math.floor(Math.random() * 10) + 12

char.wounds = 2
char.health = Math.floor(Math.random() * 10) + 11

if (char.charclass == 'Marine'){
    char.combat += 10
    char.body += 10
    char.fear += 20
    char.wounds = 3
    
	skills = remove(skills,'Military Training')
	skills = remove(skills,'Athletics')
	var randSkill = choice(skills)
	skills = remove(skills,randSkill)
  char.skills = 'Military Training, Athletics, ' + choice(['and ' + choice(['Tactics', 'Wilderness Survival', 'Firearms', 'Hand-to-Hand Combat']), 
                                                               randSkill + ', and ' + choice(skills)])
    
	char.loadout = choice(['Tank Top and Camo Pants (AP 1), Combat Knife (as Scalpel), Stimpak x1',
                'Advanced Battle Dress (AP 10), Flame Thrower, Boarding Axe',
                'Standard Battle Dress (AP 7), Combat Shotgun (4 rnds), Rucksack, Camping Gear',
                'Standard Battle Dress (AP 7), Pulse Rifle (3 mags), Infrared Goggles',
                'Standard Battle Dress (AP 7), Smart Rifle (3 mags), Binoculars, Personal Locator',
                'Standard Battles Dress (AP 7), SMG (3 mags), MRE x7',
                'Fatigues (AP 2), Combat Shotgun (2 rnds), Dog, Leash, Tennis Ball',
                'Fatigues (AP 2), Revolver (12 rnds), Single Frag Grenade',
                'Dress Uniform (AP 1), Revolver (1 rnd), Challenge Coin',
                'Advanced Battle Dress (AP 10), Heavy Machine Gun (1 can of ammo), HUD])'])
}

if (char.charclass == 'Android'){
    char.intellect += 20
    char.fear += 60
    char.wounds = 3
    var mod_stat = choice(['strength','speed','intellect','combat'])
    char[mod_stat] -= 10
    
	skills = remove(skills,'Linguistics')
	skills = remove(skills,'Computers')
	skills = remove(skills,'Mathematics')
	var randSkill = choice(skills)
	skills = remove(skills,randSkill)
    char.skills = 'Linguistics, Computers, Mathematics, ' + choice(['and ' + choice(['Hacking','Physics']),
                                                                       randSkill + ', and ' + choice(skills)])
    
	char.loadout = choice(['Vaccsuit (AP 3), Smart Rifle (2 mags), Infrared Goggles, Mylar Blanket',
                'Vaccsuit (AP 3), Revolver (12 rnds), Long-range Comms, Satchel',
                'Hazard Suit (AP 5), Revolver (6 rnds), Defibrillator, First Aid Kit, Flashlight',
                'Hazard Suit (AP 5), Foam Gun (2 charges), Sample Collection Kit, Screwdriver',
                'Standard Battle Dress (AP 7), Tranq Pistol (3 shots), Paracord (100m)',
                'Standard Crew Attire (AP 1), Stun Baton, Small Pet',
                'Standard Crew Attire (AP 1), Scalpel, Bioscanner',
                'Standard Crew Attire (AP 1), 1 Frag Grenade, Pen Knife',
                'Manufacturer Supplied Attire (AP 1), 1 Jump-9 Ticket (blank)',
                'Corporate Attire (AP 1), VIP Corporate Key Card'])
}
    
if (char.charclass == 'Scientist'){
    char.intellect += 10
    char.sanity += 30
    var mod_stat = choice(['strength','speed','intellect','combat'])
    char[mod_stat] += 5

    var doctorate = choice(['Sophontology', 'Exobiology', 'Surgery', 'Planetology', 'Robotics', 'Engineering',
                        'Cybernetics', 'Artificial Intelligence', 'Hyperspace', 'Xenoesotericism'])
    
    var masters = choice({'Sophontology': ['Psychology'], 'Exobiology': ['Pathology'], 'Surgery': ['Pathology', 'Field Medicine'],
                      'Planetology': ['Ecology', 'Asteroid Mining'], 'Robotics': ['Mechanical Repair'], 'Engineering': ['Mechanical Repair'],
                      'Cybernetics': ['Mechanical Repair'], 'Artificial Intelligence': ['Hacking'],
                      'Hyperspace': ['Piloting', 'Physics', 'Mysticism'], 'Xenoesotericism': ['Mysticism']}[doctorate])
    
    var bach = choice({'Psychology': ['Zoology'], 'Pathology': ['Zoology', 'Botany'], 'Field Medicine': ['Zoology', 'Botany'],
                   'Ecology': ['Botany', 'Geology'], 'Asteroid Mining': ['Geology', 'Industrial Equipment'],
                   'Mechanical Repair': ['Industrial Equipment', 'Jury-Rigging', 'Chemistry', 'Military Training'], 'Hacking': ['Computers'],
                   'Piloting': ['Zero-G'], 'Physics': ['Mathematics'], 'Mysticism': ['Art', 'Archaeology', 'Theology']}[masters])

    skills = remove(skills,bach)
    
    char.skills = bach + ', ' + masters + ', and ' + doctorate + '; and also ' + choice(skills)

    char.loadout = choice(['Hazard Suit (AP 5), Tranq Pistol (3 charges), Bioscanner, Sample Collection Kit',
                'Hazard Suit (AP 5), Flamethrower (1 charge), Pain Pills, Electronic Tool Set',
                'Vaccsuit (AP 3), Rigging Gun, Sample Collection Kit, Flashlight, Lab Rat',
                'Vaccsuit (AP 3), Foam Gun (2 charges), Foldable Stretcher, First Aid Kit, Radiation Pills',
                'Lab Coat (AP 1), Screwdriver, Medscanner, Vaccine (1 dose)',
                'Lab Coat (AP 1), Cybernetic Diagnostic Scanner, Portable Computer Terminal',
                'Scrubs (AP 1), Scalpel, Automed x6, Oxygen Tank with Filter Mask',
                'Scrubs (AP 1), Vial of Acid, Mylar Blanket, First Aid Kit',
                'Standard Crew Attire (AP 1), Utility Knife, Cybernetic Diagnostic Scanner, Duct Tape',
                'Civilian Clothes (AP 1), Briefcase, Prescription Pad, Fountain Pen (Poison Injector)'])
}

if (char.charclass == 'Teamster'){
    char.strength += 5
    char.speed += 5
    char.intellect += 5
    char.combat += 5
    char.sanity += 10
    char.fear += 10
    char.body += 10
    
	skills = remove(skills,'Industrial Equipment')
	skills = remove(skills, 'Zero-G')
  var jobSkill = choice(skills)
	skills = remove(skills,jobSkill)
  var jobAdvanced = {'Linguistics': [], 'Zoology': ['Psychology', 'Pathology', 'Field Medicine'],
                   'Botany': ['Pathology', 'Field Medicine', 'Ecology', 'Wilderness Survival'],'Geology': ['Ecology', 'Asteroid Mining'],
                   'Jury-Rigging': ['Mechanical Repair', 'Explosives'], 'Chemistry': ['Mechanical Repair', 'Explosives', 'Pharmacology'],
                   'Computers': ['Hacking'], 'Mathematics': ['Physics'], 'Art': ['Mysticism'], 'Archaeology': ['Mysticism'],
                   'Theology': ['Mysticism'], 'Military Training': ['Mechanical Repair', 'Explosives', 'Tactics', 'Wilderness Survival', 'Firearms'],
                   'Rimwise': ['Firearms', 'Hand-to-Hand Combat'], 'Athletics': ['Hand-to-Hand Combat']}[jobSkill]

  char.skills = 'Industrial Equipment, Zero-G, ' + jobSkill + ', and ' + choice(['Asteroid Mining', 'Mechanical Repair', 'Piloting'].concat(jobAdvanced))

	char.loadout = choice(['Vaccsuit (AP 3), Laser Cutter (charged), Patch Kit, Extra Battery',
                'Vaccsuit (AP 3), Revolver (6 rnds), Crowbar, Flashlight',
                'Vaccsuit (AP 3), Rigging Gun, Shovel, Salvage Drone',
                'Hazard Suit (AP 5), Vibechete, Spanner, Camping Gear, Water Filter',
                'Heavy Duty Work Clothes (AP 2), Explosive Charge, Detonator, Cigarettes',
                'Heavy Duty Work Clothes (AP 2), Drill, Paracord (100m), Drone',
                'Standard Crew Attire (AP 1), Combat Shotgun (4 rnds), Extension Cord (20m), Cat',
                'Standard Crew Attire (AP 1), Nail Gun (32 rnds), Head Lamp, Satchel',
                'Standard Crew Attire (AP 1), Flare Gun (2 rnds), Water Filter, Personal Locator, Subsurface Scanner',
                'Lounge Wear (AP 1), Crowbar, Pain Pills, Six Pack of Beer'])
}                                                                               
    
char.trinket = choice(['Manual: PANIC: Harbinger of Catastrophe','Pendant: Shell Fragments Suspended in Plastic',
                    'Coffee Cup, Chipped, reads: HAPPINESS IS MANDATORY','Antique Company Script (Asteroid Mine)',
                    'Pamphlet: Zen and the Art of Cargo Arrangement','Manual: Moonshining With Gun Oil & Fuel',
                    'Manual: SURVIVAL: Eat Soup With a Knife','Pair of Shot Glasses (Spent Shotgun Shells)',
                    'Miniature Chess Set, Bone, Pieces Missing','Dessicated Husk Doll', 'Key (Childhood Home)','Gyroscope, Bent, Tin',
                    'Alien Pressed Flower (common)', 'Dog Tags (Heirloom)', 'Faded Green Poker Chip','Necklace of Shell Casings',
                    'Token: “Is Your Morale Improving?”', 'Ukulele','Corroded Android Logic Core', 'Phosphorescent Sticks, Neon',
                    'Spray Paint','Pamphlet: Signs of Parasitical Infection', 'Pamphlet: The Indifferent Stars',
                    'Wanted Poster, Weathered','Manual: Treat Your Rifle Like A Lady', 'Calendar: Military Battles',
                    'Locket, Hair Braid','Bone Knife', 'Manual: Rich Captain, Poor Captain', 'Scultpure of a Rat (Gold)',
                    'Calendar: Alien Pin-Up Art', 'Campaign Poster (Home Planet)', 'Blanket, Fire Retardant',
                    'Rejected Application (Colony Ship)', 'Preserved Insectile Aberration', 'Hooded Parka, Fleece-Lined',
                    'Holographic Serpentine Dancer', 'Titanium Toothpick', 'Gun','Snake Whiskey', 'Gloves, Leather (Xenomorph Hide)',
                    'Flint Hatchet','Medical Container, Purple Powder', 'Smut (Seditious): The Captain, Ordered',
                    'Pendant: Two Astronauts form a Skull','Pills: Male Enhancement, Shoddy', 'Towel, Slightly Frayed', 'Rubik\'s Cube',
                    'Casino Playing Cards', 'Brass Knuckles', 'Stress Ball, reads: Zero Stress in Zero G','Lagomorph Foot',
                    'Fuzzy Handcuffs', 'Sputnik Pin','Moonstone Ring', 'Journal of Grudges', 'Ushanka','Manual: Mining Safety and You',
                    'Stylized Cigarette Case', 'Trucker Cap, Mesh, Grey Alien Logo','Pamphlet: Against Human Simulacrum',
                    'Ball of Assorted Gauge Wire', 'Menthol Balm','Animal Skull, 3 Eyes, Curled Horns', 'Spanner', 'Pith Helmet',
                    'Bartender’s Certification (Expired)', 'Switchblade, Ornamental', '10m x10m Tarp','Bent Wrench',
                    'Powdered Xenomorph Horn', 'I Ching, Missing Sticks','Prospecting Mug, Dented', 'Bonsai Tree, Potted', 'Kukri',
                    'Eerie Mask', 'Golf Club (Putter)', 'Trench Shovel','Ultrablack Marble', 'Trilobite Fossil',
                    'Shiv, Sharpened Butter Knife','Ivory Dice', 'Pamphlet: A Lover In Every Port', 'Taxidermied Cat',
                    'Tarot Cards, Worn, Pyrite Gilded Edges', 'Patched Overalls, Personalized', 'Pamphlet: Interpreting Sheep Dreams',
                    'Bag of Assorted Teeth', 'Fleshy Thing Sealed in a Murky Jar', 'Faded Photograph, A Windswept Heath',
                    'Ashes (A Relative)', 'Spiked Bracelet', 'Opera Glasses','DNR Beacon Necklace', 'Harmonica',
                    'Pamphlet: Android Overlords','Cigarettes (Grinning Skull)', 'Pictorial Pornography, Dogeared, Well-thumbed',
                    'Pamphlet: The Relic of Flesh','Pills: Areca Nut'])

char.patch = choice(['“I’m Not A Rocket Scientist / But You’re An Idiot”', '“I Like My Tools Clean / And My Lovers Dirty”',
                '“All Out of Fucks To Give” (Astronaut with Turned Out Pockets)', 'Medic Patch (Skull and Crossbones over Cross)',
                'Pin-Up (Nurse): “The Louder You Scream the Faster I Come”', '“Travel To Distant Places / Meet Unusual Things / Get Eaten”',
                '“Don’t Run, You’ll Only Die Tired” Backpatch', 'HMFIC (Head Mother Fucker In Charge)', 'BOHICA (Bend, Over Here It Comes Again)',
                'Red Shirt Logo', 'Dove in Crosshairs', '“I Am My Brother’s Keeper”', 'Blood Type (Reference Patch)', 'Chibi Cthulhu', '“Mama Tried”',
                'Poker Hand: Dead Man’s Hand', '“Welcome to the DANGER ZONE”', 'Black Widow Spider', 'Biohazard Symbol', 'Skull and Crossed Wrenches',
                '“My Other Ride Married You”', 'Mr. Yuck', 'Pin-Up (Succubus)', '“One Size Fits All” (Grenade)', 'Nuclear Symbol', '“DILLIGAF?”',
                'Grim Reaper Backpatch', '“Eat The Rich”', '“DRINK / FIGHT / FUCK”', 'отъебись (Get Fucked, Russian)', '“Be Sure: Doubletap”',
                '“Work Hard / Party Harder”', '“Smooth Operator”', 'Flame Emoji', 'Mudflap Girl', 'Atom Symbol', 'Smiley Face (Glow in the Dark)',
                'Fun Meter (reads: Bad Time)', '“For Science!”', '“Smile: Big Brother is Watching”', '“GAME OVER” (Bride & Groom)', '“Actually, I AM A Rocket Scientist”',
                'Jolly Roger', 'Heart', '“Help Wanted”', 'Viking Skull', '“IMPROVE / ADAPT / OVERCOME”', 'Princess', '“APEX PREDATOR” (Sabertooth Skull)',
                '“SUCK IT UP”', '“NOMAD”', 'Pin-Up (Ace of Spades)', '“Cowboy Up” (Crossed Revolvers)', '“GOOD BOY”', 'Queen of Hearts', '“Troubleshooter”',
                'Dice (Snake Eyes)', 'Security Guard', 'NASA Logo', '“#1 Worker”', '“LONER”', 'Crossed Hammers with Wings', '“Good” (Brain)',
                'Front Towards Enemy (Claymore Mine)', '“Keep Well Lubricated”', '“Bad Bitch”', 'Pin-Up (Riding Missile)', 'Soviet Hammer & Sickle',
                '“Too Pretty To Die”', 'FUBAR', '“Plays Well With Others”', '“Fuck Forever” (Roses)', '“I’m A (Love) Machine”', '“Live Free and Die”', 'Icarus',
                'Pin-Up (Mechanic)', '“IF I’M RUNNING KEEP UP” Backpatch', '”Girl’s Best Friend” (Diamond)', 'HELLO MY NAME IS:', '“Meat Bag”',
                'Risk of Electrocution Symbol', '“Powered By Coffee”', '“I Am Not A Robot”', 'Inverted Cross', '“Take Me To Your Leader” (UFO)', 'Red Gear',
                '“Do You Sign My Paychecks?” Backpatch', '“DO YOUR JOB”', '“I Can’t Fix Stupid”', '“I ♥ Myself”', '“Take My Life (Please)”',
                '“Space IS My Home” (Sad Astronaut)', 'Double Cherry', '“Upstanding Citizen”', 'All Seeing Eye', '“Volunteer”',
                'Allergic To Bullshit (Medical Style Patch)', '“Do I LOOK Like An Expert?”', '“Solve Et Coagula” (Baphomet)', '“Fix Me First” (Caduceus)'])


document.getElementById("demo").innerHTML ="You are ${(char.charclass == 'Android') ? 'an' : 'a'} ${char.charclass}. Your stats are: \n STR: ${char.strength}, SPD: ${char.speed}, INT: ${char.intellect}, CMB: ${char.combat} \n SAN: ${char.sanity}, FER: ${char.fear}, BOD: ${char.body} \n You have ${char.wounds} wounds with ${char.health} health each and start with 2 stress. \n  \n You're carrying: ${char.loadout}, as well as a ${char.trinket}. \n Your skills are ${char.skills}. \n  \n On your uniform, you wear a ${char.patch} patch.";

})();


}
</script>

</body>
</html>


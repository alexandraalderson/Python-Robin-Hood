PROGRAM ROBIN_HOOD_MIDNIGHT_GOLD

    # Main game procedure – introduces the story and calls the first decision
    PROCEDURE START_GAME
        SEND "Robin Hood: Midnight Gold" TO DISPLAY
        SEND "The moon hangs low over Sherwood Forest. Owls call across the dark canopy." TO DISPLAY
        SEND "You, Robin Hood, crouch near a mossy oak beside Little John and Maid Marian." TO DISPLAY
        SEND "Scouts whisper that the Sheriff's gold convoy will pass through the forest within the hour." TO DISPLAY
        SEND "Your mission: outsmart the Sheriff and deliver the gold to Nottingham's poor." TO DISPLAY

        # Call the first decision procedure
        CALL DECISION_A
    ENDPROCEDURE


    # Decision A – player chooses the first move
    PROCEDURE DECISION_A
        SEND "Quick! Make your first move:" TO DISPLAY
        SEND "1. Scout the convoy first" TO DISPLAY
        SEND "2. Set a trap immediately" TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL BRANCH_A1          # Go to scouting branch
        ELSE IF choice = "2" THEN
            CALL BRANCH_A2          # Go to trap branch
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A         # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Branch A1 – scouting path introduction
    PROCEDURE BRANCH_A1
        SEND "You slip through the trees like a shadow." TO DISPLAY
        SEND "From a ridge you see torches flicker: four wagons of gold, guarded by a dozen soldiers." TO DISPLAY
        SEND "You overhear their route and timing and return to the hideout." TO DISPLAY

        # Proceed to the next tactic decision
        CALL DECISION_A1
    ENDPROCEDURE


    # Decision A1 – choose the next tactic after scouting
    PROCEDURE DECISION_A1
        SEND "What will be your next tactic?" TO DISPLAY
        SEND "1. Ambush at the stone bridge" TO DISPLAY
        SEND "2. Sneak into the camp at night" TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL PATH_A1B1          # Go to ambush path
        ELSE IF choice = "2" THEN
            CALL PATH_A1B2          # Go to sneak path
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A1         # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Path A1B1 – ambush at the stone bridge
    PROCEDURE PATH_A1B1
        SEND "The wagons clatter across the old stone bridge." TO DISPLAY
        SEND "At your signal, ropes snap tight. The first cart overturns, blocking the way." TO DISPLAY
        SEND "Your archers rain arrows on the startled guards. The Sheriff's men surrender without a fight." TO DISPLAY

        # Proceed to the final action decision
        CALL DECISION_A1B1
    ENDPROCEDURE


    # Decision A1B1 – final action after a successful ambush
    PROCEDURE DECISION_A1B1
        SEND "It's your big moment - what's your final action?" TO DISPLAY
        SEND "1. Free the prisoners and send the gold to the poor." TO DISPLAY
        SEND "2. Take a share and vanish into Sherwood." TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL END1              # Success ending
        ELSE IF choice = "2" THEN
            CALL END2              # Failure ending
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A1B1      # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Path A1B2 – sneak into the Sheriff's camp
    PROCEDURE PATH_A1B2
        SEND "Night falls. You creep into the Sheriff's camp." TO DISPLAY
        SEND "A twig snaps under Little John's boot. The camp erupts in shouts and flashing steel." TO DISPLAY

        # Proceed to fight or escape decision
        CALL DECISION_A1B2
    ENDPROCEDURE


    # Decision A1B2 – fight or escape from the camp
    PROCEDURE DECISION_A1B2
        SEND "Quick, what will you do?!" TO DISPLAY
        SEND "1. Fight" TO DISPLAY
        SEND "2. Escape empty-handed" TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL END3              # Failure ending
        ELSE IF choice = "2" THEN
            CALL END4              # Failure ending
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A1B2      # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Branch A2 – set a trap immediately
    PROCEDURE BRANCH_A2
        SEND "Without scouting, you and your band rush to rig ropes and spikes along the forest road." TO DISPLAY
        SEND "The night air hums with urgency. You hope you have chosen the right path." TO DISPLAY

        # Proceed to ambush style decision
        CALL DECISION_A2
    ENDPROCEDURE


    # Decision A2 – choose ambush style
    PROCEDURE DECISION_A2
        SEND "Decision A2 – Ambush Style" TO DISPLAY
        SEND "1. Hide nearby and wait" TO DISPLAY
        SEND "2. Send Little John as a decoy" TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL END5              # Failure ending
        ELSE IF choice = "2" THEN
            CALL PATH_A2B3         # Proceed to decoy branch
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A2        # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Path A2B3 – send Little John as a decoy
    PROCEDURE PATH_A2B3
        SEND "Little John strolls into the road singing loudly." TO DISPLAY
        SEND "But the Sheriff anticipated the ploy: hidden crossbowmen leap from the shadows." TO DISPLAY

        # Proceed to last stand or surrender decision
        CALL DECISION_A2B3
    ENDPROCEDURE


    # Decision A2B3 – last stand or surrender
    PROCEDURE DECISION_A2B3
        SEND "Choose: make your last stand or surrender." TO DISPLAY
        SEND "1. Last stand - fight." TO DISPLAY
        SEND "2. Give in and surrender." TO DISPLAY

        # Receive and check the user's choice
        RECEIVE choice FROM (STRING) KEYBOARD

        IF choice = "1" THEN
            CALL END3              # Failure ending
        ELSE IF choice = "2" THEN
            CALL END6              # Failure ending
        ELSE
            SEND "Please enter 1 or 2." TO DISPLAY
            CALL DECISION_A2B3      # Ask again until input is valid
        ENDIF
    ENDPROCEDURE


    # Ending procedures – display final outcome messages
    PROCEDURE END1
        SEND "SUCCESS!" TO DISPLAY
        SEND "Cheers rise in Nottingham as bread and coins feed every hungry family." TO DISPLAY
        SEND "The people sing ballads of Robin Hood's midnight victory." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE

    PROCEDURE END2
        SEND "FAILURE." TO DISPLAY
        SEND "Guards regroup and pursue. The Sheriff swears vengeance, and the poor remain hungry." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE

    PROCEDURE END3
        SEND "FAILURE." TO DISPLAY
        SEND "Outnumbered, you and your band are captured." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE

    PROCEDURE END4
        SEND "FAILURE." TO DISPLAY
        SEND "You save your lives but lose the gold." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE

    PROCEDURE END5
        SEND "FAILURE." TO DISPLAY
        SEND "The convoy looks like it will pass directly into your unscouted trap." TO DISPLAY
        SEND "The ropes tighten perfectly, overturning the first cart." TO DISPLAY
        SEND "However another highwayman ambushes them before you can get there and steals the gold." TO DISPLAY
        SEND "You would have seen them if you had checked more thoroughly." TO DISPLAY
        SEND "You leave with nothing." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE

    PROCEDURE END6
        SEND "FAILURE." TO DISPLAY
        SEND "Chains and the dungeon await." TO DISPLAY
        SEND "Game Over." TO DISPLAY
    ENDPROCEDURE


    # Main program starts here
    CALL START_GAME

ENDPROGRAM

# Requirements

1. WHEN the app loads THE SYSTEM SHALL restore energy, owned unlockables (snacks, music1, music2, music3, music4, music5), and current track index from `localStorage` if present, or initialize defaults (energy = 0, all unlockables locked, trackIndex = 0) if not.
2. WHEN the user taps the character THE SYSTEM SHALL increase energy by 1, play a tap animation & sound effect on the character, and update the energy counter.
3. WHEN energy changes THE SYSTEM SHALL persist the new energy value to `localStorage`.
4. WHEN an unlockable's cost is greater than the current energy THE SYSTEM SHALL display it in a locked state with its cost shown and its unlock control disabled.
5. WHEN an unlockable's cost is less than or equal to the current energy AND it is not yet owned THE SYSTEM SHALL enable its unlock control.
6. WHEN the user activates an enabled unlock control THE SYSTEM SHALL deduct the unlockable's cost from energy, mark it as owned, play an unlock chime, display one of its dialogue lines in the dialogue bubble, start playing that track if it's music, and persist the change to `localStorage`.
7. WHEN any of the music unlockables (`music1`–`music5`) is owned THE SYSTEM SHALL display the music disc widget. WHILE none is owned THE SYSTEM SHALL keep the disc widget hidden.
8. WHEN the user clicks the disc or next control THE SYSTEM SHALL advance to the next unlocked YouTube track (wrapping to the first after the last), update the displayed track title and artist, show a "now playing" dialogue line, and persist the new track index to `localStorage`.
9. WHEN a dialogue line is shown THE SYSTEM SHALL automatically hide it a few seconds later.
10. WHERE the browser window is a mobile width THE SYSTEM SHALL keep all controls usable without horizontal scrolling.

1. Reflekter kort men fagligt over din løsning med henblik på udfordringerne og successerne ved opgaven.

Min startede med at kode komponenterne fra Figma-Mockup'en separat, så de kunne genbruges og nemt integreres på de forskellige sider. Dog blev min udfordring hurtigt at sikre præcisionen i designet og implementere et responsivt layout, samt at holde overblik over forksekllige css-regler der ikke overskriver hinanden. 
Jeg fik delvist implementere en responsiv tilgang, ved at bruge @media queryies - dog fungere det ikke helt optimalt alle steder på sitet. 
Jeg stødte på en frustrerende fejl, hvor mine ikoner ikke blev vist korrekt på Netlify. Fejlmeddelelsen nævnte, at `checkmark.svg` på en eller anden måde refererede til sig selv og ikke blev håndteret rigtigt under build-processen. Jeg prøvede at tjekke, om filen lå det rigtige sted, og forsøgte også at ekskludere den i `astro.config.mjs`, men problemet er der stadig. Det har været en udfordring at forstå, hvordan Astro behandler statiske filer i produktion, og jeg er stadig ikke helt sikker på, hvad der præcist går galt.



2. Fremhæv specifikke kodestumper, der illustrerer brugen af forskellige teknikker og principper (gerne fra undervisningen).

    Ved brugen af "&" til at neste ".primary" og ":hover" under ".button", undgår vi gentagelse og gør koden mere læsbar og vedligeholdelsesvenlig.
    .button {
      border-radius: 1.25rem;
      padding: 0.25rem 1rem;
      place-self: center;
      font-family: var(--font-primary);
      font-weight: var(--font-weight-bold);

      &.primary {
        color: var(--primary03-color);
        background: var(--primary01-color);

        &:hover {
          background-color: var(--primary-hover, #ffe5a2);
        }
      }
    }
    ________________

    Jeg har brugt nesting for at holde relaterede styles samlet, hvilket gør koden mere overskuelig og nemmere at læse. Fx ligger .container inde i section, fordi den kun bruges dér.
    @layer hjælper med at organisere CSS’en bedre ved at gruppere mine styles i forskellige lag. Her har jeg placeret komponent-specifik CSS i @layer components, så den ikke konflikter med globale styles.

     @layer components {
        .what-to-expect {
            position: relative;
            margin-top: 100px;
            z-index: 1;
        }

        section {
            display: inline-flex;
            align-items: flex-start;
            gap: 5.125rem;
            margin: 5rem 2rem;

            /* Nested container styles */
            .container {
                flex-direction: column;
                max-width: 30.0625rem;
                z-index: 2;
            }
        }
    }

3. Forklar, hvordan du har organiseret din CSS; hvornår er det globalt, og hvornår er det komponent-specifikt.
Jeg har organiseret min CSS ved at holde generelle styles globalt, mens specifikke styles ligger i de enkelte komponenter. 
Men jo længere jeg kom i opgaven, jo mindre overblik havde jeg. 
Jeg fandt nogle smartere måder at gøre tingene på, men ofte først efter, at jeg allerede havde kodet det på en anden måde. Det gjorde det svært at gå tilbage og rydde helt op, så nogle ting endte med at være lidt blandet sammen.


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StateZer0 | Technical White Paper (v76.0.0)</title>
    <style>
        /* MOBILE-FIRST LAYOUT FIX - PRESERVED */
        * { box-sizing: border-box; }

        body {
            background-color: #EDE6D6;
            color: #1a1a1a;
            font-family: 'Georgia', serif;
            line-height: 1.7;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        .document-container {
            background-color: #ffffff;
            width: 100%;
            max-width: 850px;
            padding: 50px 40px;
            border: 1px solid #D2D2B4;
            border-radius: 4px;
            box-shadow: 10px 10px 0px rgba(0,0,0,0.05);
            overflow-wrap: break-word;
            margin: 0 auto;
        }

        /* TRANSLATION TOGGLE STYLING */
        .lang-switch {
            text-align: right;
            margin-bottom: 20px;
            font-family: 'Courier New', monospace;
            font-weight: bold;
        }
        .lang-btn {
            cursor: pointer;
            padding: 5px 10px;
            border: 1px solid #1a1a1a;
            background: #fff;
            transition: 0.2s;
        }
        .lang-btn.active {
            background: #1a1a1a;
            color: #fff;
        }

        html[lang="de"] [lang="en"] { display: none; }
        html[lang="en"] [lang="de"] { display: none; }

        .header-branding { text-align: center; margin-bottom: 40px; }
        .header-branding img { max-width: 180px; height: auto; }
        .contact-line { margin-top: 15px; font-family: 'Courier New', Courier, monospace; font-weight: bold; font-size: 0.9em; letter-spacing: 1px; }
        .header-divider { border-bottom: 2px solid #1a1a1a; width: 40%; margin: 20px auto; }

        h1 { text-align: center; font-size: 2.2em; text-transform: uppercase; letter-spacing: 4px; margin-bottom: 10px; line-height: 1.2; }
        .subtitle { text-align: center; font-size: 1.1em; font-weight: bold; letter-spacing: 2px; margin-bottom: 40px; opacity: 0.7; }

        h2 { color: #27ae60; border-left: 6px solid #27ae60; padding-left: 15px; margin-top: 50px; text-transform: uppercase; font-size: 1.3em; }
        h3 { font-size: 1.1em; color: #1a1a1a; margin-top: 25px; margin-bottom: 10px; }

        p, li { font-size: 1.05em; color: #222; text-align: justify; }
        ul { list-style-type: square; padding-left: 20px; }
        li { margin-bottom: 15px; }

        .warning-box { background: #1a1a1a; color: #fff; padding: 20px; margin: 40px 0; font-weight: bold; text-transform: uppercase; text-align: center; border: 2px solid #e74c3c; }
        .status-footer { margin-top: 80px; text-align: center; font-size: 1.1em; font-weight: bold; border-top: 1px solid #1a1a1a; padding-top: 20px; }

        @media (max-width: 600px) {
            h1 { font-size: 1.6em; letter-spacing: 1px; word-break: keep-all; }
            .subtitle { font-size: 0.9em; letter-spacing: 1px; line-height: 1.4; }
            .document-container { padding: 30px 20px; }
            body { padding: 10px; }
        }
    </style>
</head>
<body>
    <div class="document-container">
        <div class="lang-switch">
            <span class="lang-btn" id="btn-en" onclick="setLang('en')">EN</span>
            <span class="lang-btn" id="btn-de" onclick="setLang('de')">DE</span>
        </div>

        <div class="header-branding">
            <img src="logo.png" alt="StateZer0 Logo">
            <div class="contact-line">
                OFFICIAL CONTACT: <a href="mailto:StateZer04U@proton.me" style="color: #1a1a1a; text-decoration: underline;">StateZer04U@proton.me</a>
            </div>
            <div class="header-divider"></div>
        </div>

                <h1>
            <span lang="en">Technical White Paper & Architectural Audit (v76.0.0-STABLE)</span>
            <span lang="de">Technisches Whitepaper & Architektur-Audit (v76.0.0-STABLE)</span>
        </h1>
        <div class="subtitle">
            <span lang="en">StateZer0: An End-to-End Encrypted Communications Platform</span>
            <span lang="de">StateZer0: Eine Ende-zu-Ende-verschlüsselte Kommunikationsplattform</span>
        </div>

                <div class="warning-box">
            <span lang="en">Date: November 15, 2026 | Project: StateZer0</span>
            <span lang="de">Datum: 15. November 2026 | Projekt: StateZer0</span><br>
            <span lang="en" style="color: #2ecc71;">[AUDIT CYCLE 76.0.0-STABLE]: Sender-Side Performance & Security Hardening (Phase 1)</span>
            <span lang="de" style="color: #2ecc71;">[AUDIT-ZYKLUS 76.0.0-STABLE]: Senderseitige Performance & Sicherheitshärtung (Phase 1)</span>
        </div>

        <h2><span lang="en">I. Executive Summary & Market Value Proposition</span><span lang="de">I. Management-Zusammenfassung & Markt-Nutzenversprechen</span></h2>

        <h3>1.1 <span lang="en">Overview</span><span lang="de">Überblick</span></h3>
        <p>
            <span lang="en">StateZer0 is a hardened communications platform that minimizes server-side data exposure. The server acts only as a relay for encrypted blobs: the operator has no visibility into message or attachment content and no access to the user's contact list. Metadata is reduced to the minimum needed for routing and is never zero. This design limits, but does not eliminate, the operator's exposure to data requests.</span>
            <span lang="de">StateZer0 ist eine gehärtete Kommunikationsplattform, die die serverseitige Datenpreisgabe minimiert. Der Server fungiert ausschließlich als Relay für verschlüsselte Blobs: Der Betreiber hat weder Einblick in Nachrichten- oder Anhangsinhalte noch Zugriff auf die Kontaktliste des Nutzers. Metadaten werden auf das für das Routing erforderliche Minimum reduziert und sind nie gleich null. Dieses Design begrenzt, beseitigt aber nicht, die Exposition des Betreibers gegenüber Datenanfragen.</span>
        </p>

        <h3>1.2 <span lang="en">Core Value Drivers</span><span lang="de">Kern-Werttreiber</span></h3>
        <ul>
            <li>
                <span lang="en"><b>Sender-Side Performance & Security Hardening (v76.0.0 - Phase 1):</b> Implemented the <b>Direct RAM Pipeline</b> for images and audio, keeping unencrypted bytes in volatile memory where feasible. For high-overhead video transcoding, transient plaintext artifacts are overwritten as a best-effort measure before deletion, reducing the chance of recoverable residue.</span>
                <span lang="de"><b>Senderseitige Performance & Sicherheitshärtung (v76.0.0 - Phase 1):</b> Implementierung der <b>Direct RAM Pipeline</b> für Bilder und Audio, die unverschlüsselte Bytes nach Möglichkeit im flüchtigen Speicher hält. Bei ressourcenintensiver Videotranskodierung werden temporäre Klartext-Artefakte vor der Löschung nach bestem Bemühen überschrieben, um wiederherstellbare Rückstände zu reduzieren.</span>
            </li>
            <li>
                <span lang="en"><b>Non-Blocking Netty Engine (v73.0.0 - Phase 3):</b> Heavy media extraction and Signal envelope hydration are offloaded to background worker pools. <code>ThumbnailExtractorEngine</code> was converted to an asynchronous service anchored to <code>Dispatchers.IO</code>, improving Main Thread responsiveness and reducing starvation risk for Netty IO selector loops during high-resolution ingestion.</span>
                <span lang="de"><b>Non-Blocking Netty-Engine (v73.0.0 - Phase 3):</b> Ressourcenintensive Medienextraktion und Signal-Envelope-Hydrierung werden in Hintergrund-Worker-Pools ausgelagert. Die <code>ThumbnailExtractorEngine</code> wurde in einen asynchronen Dienst umgewandelt, der an <code>Dispatchers.IO</code> verankert ist, um die Reaktionsfähigkeit des Android Main Threads zu verbessern und das Starvation-Risiko der Netty-IO-Selector-Loops während der hochauflösenden Ingestion zu verringern.</span>
            </li>
            <li>
                <span lang="en"><b>Sovereign Blinding (v25.2.7):</b> Sensitive identifiers are pre-blinded on the Android client before they reach the relay. The relay acts as an encrypted-blob relay: it routes opaque pointers but does not have access to message or attachment content and does not maintain a social graph.</span>
                <span lang="de"><b>Souveräne Verblindung (v25.2.7):</b> Sensitive Identifikatoren werden auf dem Android-Client vorverblindet, bevor sie das Relay erreichen. Das Relay fungiert als verschlüsselter-Blob-Relay: Es leitet opake Pointer weiter, hat aber keinen Zugriff auf Nachrichten- oder Anhangsinhalte und pflegt keinen sozialen Graphen.</span>
            </li>
            <li>
                <span lang="en"><b>Metadata Minimization (v25.2.7):</b> Identifying metadata (e.g., <i>legacyId</i>) is hashed or removed before it leaves the client and is stored only in encrypted form where the server needs it for routing. MongoDB fields are encrypted at rest with AES-256-GCM using <code>GHOST_FIELD_KEY</code>.</span>
                <span lang="de"><b>Metadaten-Minimierung (v25.2.7):</b> Identifizierende Metadaten (z. B. <i>legacyId</i>) werden gehasht oder entfernt, bevor sie den Client verlassen, und nur verschlüsselt dort gespeichert, wo der Server sie für das Routing benötigt. MongoDB-Felder sind mit AES-256-GCM unter Verwendung von <code>GHOST_FIELD_KEY</code> verschlüsselt.</span>
            </li>
            <li>
                <span lang="en"><b>Opaque Sync (v25.2.7):</b> Message synchronization requests use client-provided opaque cursors. The relay stores message payloads as encrypted blobs and does not interpret their content; routing metadata is minimized to what is required for delivery.</span>
                <span lang="de"><b>Opaker Sync (v25.2.7):</b> Anfragen zur Nachrichtensynchronisation verwenden clientseitig bereitgestellte opake Cursor. Das Relay speichert Nachrichten-Payloads als verschlüsselte Blobs und interpretiert deren Inhalt nicht; Routing-Metadaten werden auf das für die Zustellung erforderliche Minimum reduziert.</span>
            </li>
            <li>
                <span lang="en"><b>Automatic State Promotion (v25.2.7):</b> Resolves connection deadlocks by automatically upgrading contacts to <b>ACCEPTED</b> upon cryptographic identity proof via trial decryption.</span>
                <span lang="de"><b>Automatische Status-Promotierung (v25.2.7):</b> Löst Verbindungs-Deadlocks, indem Kontakte bei kryptografischem Identitätsnachweis über Trial Decryption automatisch auf <b>ACCEPTED</b> hochgestuft werden.</span>
            </li>
            <li>
                <span lang="en"><b>Backend Storage (v53.2.0):</b> The backend (Ktor/Netty/MongoDB) stores message and attachment payloads as opaque encrypted blobs. Persistent fields are encrypted at rest with AES-256-GCM using <code>GHOST_FIELD_KEY</code>. The relay does not maintain a <i>contacts</i> collection or social graph; it only keeps the minimal routing data required to deliver encrypted blobs.</span>
                <span lang="de"><b>Backend-Speicher (v53.2.0):</b> Das Backend (Ktor/Netty/MongoDB) speichert Nachrichten- und Anhangs-Payloads als opake verschlüsselte Blobs. Persistente Felder sind mit AES-256-GCM unter Verwendung von <code>GHOST_FIELD_KEY</code> verschlüsselt. Das Relay pflegt keine <i>contacts</i>-Sammlung und keinen sozialen Graphen; es hält nur die für die Zustellung verschlüsselter Blobs erforderlichen Mindest-Routingdaten.</span>
            </li>
            <li>
                <span lang="en"><b>Client-Side Identity Autonomy:</b> Identity is established via 256-bit local entropy (BIP39), removing the need for phone numbers or email addresses—the primary vectors for state-level deanonymization.</span>
                <span lang="de"><b>Clientseitige Identitätsautonomie:</b> Die Identität wird über eine lokale 256-Bit-Entropie (BIP39) etabliert, wodurch Telefonnummern oder E-Mail-Adressen – die primären Vektoren für staatliche Deanonymisierung – überflüssig werden.</span>
            </li>
            <li>
                <span lang="en"><b>Modular Outbound Media (v29.0.0):</b> Specialized processors handle domain-specific security logic (e.g., StaticImageProcessor for EXIF scrubbing, VideoProcessor for reliable poster extraction). This modularity prevents logic bleed and keeps cryptographic handling isolated for each media type.</span>
                <span lang="de"><b>Modulare Outbound-Medien (v29.0.0):</b> Spezialisierte Prozessoren verarbeiten domänenspezifische Sicherheitslogik (z. B. StaticImageProcessor für EXIF-Bereinigung, VideoProcessor für zuverlässige Poster-Extraktion). Diese Modularität verhindert „Logic Bleed“ und hält die kryptografische Verarbeitung für jeden Medientyp isoliert.</span>
            </li>
            <li>
                <span lang="en"><b>MIME & Lifecycle Stabilization (v28.0.2):</b> Hardened the media pipeline against system-level misclassification. Videos now utilize extension-priority sniffing to ensure reliable container resolution and bypass incorrect optimization paths.</span>
                <span lang="de"><b>MIME- & Lifecycle-Stabilisierung (v28.0.2):</b> Die Medien-Pipeline wurde gegen systemseitige Fehlklassifizierungen gehärtet. Videos nutzen nun eine Extension-Priority-Prüfung, um eine zuverlässige Container-Auflösung zu gewährleisten und falsche Optimierungspfade zu umgehen.</span>
            </li>
            <li>
                <span lang="en"><b>Hardened Phase 3 Isolation & Stable Identity (v64.0.0):</b> Integrated strict <b>ImageViewTarget</b> guarding across all media adapters to block stale bitmaps during rapid view recycling. Refactored the UI diffing engine to utilize <b>Stable Identity Anchors</b> (attachmentUuid), ensuring visual continuity and eradicating flickering during server-side ID finalization and state transitions.</span>
                <span lang="de"><b>Gehärtete Phase-3-Isolierung & Stabile Identität (v64.0.0):</b> Integration von striktem <b>ImageViewTarget</b>-Guarding über alle Medienadapter hinweg, um veraltete Bitmaps während schnellem View-Recycling zu blockieren. Refactoring der UI-Diffing-Engine zur Nutzung von <b>stabilen Identitätsankern</b> (attachmentUuid), was eine zuverlässige visuelle Kontinuität gewährleistet und Flimmern während der serverseitigen ID-Finalisierung sowie bei Statusübergängen eliminiert.</span>
            </li>
            <li>
                <span lang="en"><b>Synchronous Sidecar Hook (v63.0.0):</b> To reduce visual jitter, StateZer0 implements <b>Synchronous Sidecar Extraction</b>. High-quality 512px previews are generated at the moment of attachment selection, so local metadata is populated before background processing begins.</span>
                <span lang="de"><b>Synchroner Sidecar-Hook (v63.0.0):</b> Um visuelles Flackern zu reduzieren, implementiert StateZer0 eine <b>synchrone Sidecar-Extraktion</b>. Hochwertige 512px-Vorschauen werden im Moment der Anhangsauswahl generiert, sodass lokale Metadaten vor Beginn der Hintergrundverarbeitung gefüllt sind.</span>
            </li>
            <li>
                <span lang="en"><b>Protocol Handshake Isolation (v50.0.5):</b> User-management and media-transport paths are separated at the transport entry point. Handshake signals are intercepted and diverted to a dedicated control path.</span>
                <span lang="de"><b>Protokoll-Handshake-Isolation (v50.0.5):</b> Benutzermanagement- und Medientransport-Pfade werden am Transport-Eintrittspunkt getrennt. Handshake-Signale werden abgefangen und auf einen dedizierten Kontrollpfad umgeleitet.</span>
            </li>
            <li>
                <span lang="en"><b>Resilience Layer Modularization (v50.1.0):</b> Strictly decoupled the transport infrastructure (WebSocket, heartbeats, noise) from message orchestration. Low-level connection management is now delegated to a specialized <code>ResilienceTransportManager</code>, air-gapping the application-level E2EE logic from transport-layer failures.</span>
                <span lang="de"><b>Resilienz-Schicht-Modularisierung (v50.1.0):</b> Strikte Entkopplung der Transport-Infrastruktur (WebSocket, Herzschläge, Rauschen) von der Nachrichten-Orchestrierung. Das Low-Level-Verbindungsmanagement wird nun an einen spezialisierten <code>ResilienceTransportManager</code> delegiert, wodurch die Applikations-E2EE-Logik von Fehlern auf der Transportschicht abgeschirmt wird.</span>
            </li>
            <li>
                <span lang="en"><b>Sovereign Document Enclave (v40.6.2):</b> Multi-document handoffs are isolated within a restricted <code>shared_staging</code> internal subfolder. External viewers receive temporary, read-only URIs via a <b>FileProvider</b>, and the staging area is cleared at startup, before handoff, and on destroy as a best-effort measure.</span>
                <span lang="de"><b>Souveräne Dokumenten-Enklave (v40.6.2):</b> Multi-Dokument-Übergaben werden innerhalb eines eingeschränkten internen <code>shared_staging</code>-Unterordners isoliert. Externe Viewer erhalten temporäre, schreibgeschützte URIs über einen <b>FileProvider</b>, und der Staging-Bereich wird beim Start, vor der Übergabe und beim Zerstören nach bestem Bemühen geleert.</span>
            </li>
            <li>
                <span lang="en"><b>Stable Rendering & Anchoring (v14.0.1):</b> The ledger uses <b>Stable Identity Anchors</b> tied to the SQLCipher primary key to reduce visual flicker during the local-to-server ID transition. The Enclave Grid uses <b>Granular DiffUtil Hydration</b>, allowing individual cell updates during background thumbnail generation without grid-wide refreshes.</span>
                <span lang="de"><b>Stabiles Rendering & Verankerung (v14.0.1):</b> Das Ledger nutzt <b>stabile Identitätsanker</b>, die an den SQLCipher-Primärschlüssel gebunden sind, um visuelles Flackern während des Übergangs von lokaler zu Server-ID zu reduzieren. Das Enklaven-Grid nutzt eine <b>granulare DiffUtil-Hydrierung</b>, die einzelne Zellen-Updates während der Hintergrund-Thumbnail-Generierung ohne gridweite Refreshes ermöglicht.</span>
            </li>
            <li>
                <span lang="en"><b>UI Surface Safety & Composite Keying (v40.0.2):</b> Implemented mandatory hardware surface resets, composite player keying (`msg_` vs `att_`), and <b>Metadata-Aware IV Hydration</b> to eliminate EGL surface contention and "black screen" decoder failures. The playback engine now supports reliable CTR-mode seeking in multi-attachment bundles, ensuring rendering integrity in high-density chat streams.</span>
                <span lang="de"><b>UI Surface Safety & Composite Keying (v40.0.2):</b> Implementierung von obligatorischen Hardware-Surface-Resets, Composite-Player-Keying (`msg_` vs `att_`) und <b>metadatengesteuerter IV-Hydrierung</b>, um EGL-Oberflächenkonflikte und „Black Screen“-Decoder-Fehler zu eliminieren. Die Playback-Engine unterstützt nun zuverlässiges CTR-Modus-Seeking in Multi-Attachment-Bundles und gewährleistet so die Rendering-Integrität in hochdichten Chat-Streams.</span>
            </li>

            <li>
                <span lang="en"><b>VoIP Engine Decoupling (v52.0.0):</b> The VoIP media stack is isolated from standard messaging and storage domains. Handshake and media setup are managed by a dedicated <code>VoipEngineController</code>. Native WebRTC components (AudioSource, AudioTrack, PeerConnection) are explicitly disposed and released when a call ends. Calls are forced through TURN as a privacy choice, which adds latency.</span>
                <span lang="de"><b>VoIP-Engine-Entkopplung (v52.0.0):</b> Der VoIP-Medienstack ist von den Standard-Messaging- und Speicherdomänen isoliert. Handshake und Medienaufbau werden von einem dedizierten <code>VoipEngineController</code> verwaltet. Native WebRTC-Komponenten (AudioSource, AudioTrack, PeerConnection) werden beim Beenden eines Anrufs explizit freigegeben und released. Anrufe werden als datenschutzorientierte Entscheidung über TURN geleitet, was die Latenz erhöht.</span>
            </li>
            <li>
                <span lang="en"><b>Limited Data Collection:</b> The relay does not store message or attachment content in plaintext and does not maintain a social graph. Minimal server logs (e.g., for abuse prevention and legal compliance) are retained for up to 30 days. Whether a particular processing activity complies with GDPR, DSA, or TDDDG depends on the specific deployment and must be assessed by the operator.</span>
                <span lang="de"><b>Begrenzte Datenerhebung:</b> Das Relay speichert keine Nachrichten- oder Anhangsinhalte im Klartext und pflegt keinen sozialen Graphen. Minimale Server-Logs (z. B. zur Missbrauchsprävention und Rechts compliance) werden bis zu 30 Tage aufbewahrt. Ob eine bestimmte Verarbeitung mit DSGVO, DSA oder TDDDG konform ist, hängt vom konkreten Betrieb ab und muss vom Betreiber geprüft werden.</span>
            </li>
        </ul>

        <h2><span lang="en">II. Encrypted Message Relay & Metadata Minimization</span><span lang="de">II. Verschlüsselter Nachrichten-Relay & Metadatenminimierung</span></h2>

        <h3>2.1 <span lang="en">Blinded Routing & Metadata Isolation</span><span lang="de">2.1 Blinded Routing & Metadaten-Isolation</span></h3>
        <p>
            <span lang="en">The StateZer0 server operates as a relay for encrypted data. Message and attachment payloads pass through the pipeline as opaque cryptographic blobs; the operator has no visibility into their content. Routing metadata is minimized, not eliminated, because delivery requires some addressing information.</span>
            <span lang="de">Der StateZer0-Server fungiert als Relay für verschlüsselte Daten. Nachrichten- und Anhangs-Payloads passieren die Pipeline als opake kryptografische Blobs; der Betreiber hat keinen Einblick in deren Inhalt. Routing-Metadaten werden minimiert, nicht eliminiert, da die Zustellung einige Adressierungsinformationen erfordert.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Blinded Recipient IDs:</b> Recipient identifiers are gehashed via SHA-256 and salted with a server-side pepper before database insertion. The relay delivers messages to these blinded pointers without knowledge of the true user identity.</span>
                <span lang="de"><b>Blinded Recipient IDs:</b> Empfängerkennungen werden vor der Datenbankeinfügung über SHA-256 gehasht und mit einem serverseitigen Pepper gesalzen. Das Relay stellt Nachrichten an diese verblindeten Pointer zu, ohne Kenntnis der wahren Benutzeridentität.</span>
            </li>
            <li>
                <span lang="en"><b>Discovery Policy Enforcement (v25.3.1):</b> Accounts are hidden from search by default. Adding a contact requires a mutual-consent invite request that the recipient can Accept or Reject. The relay does not maintain a social graph and cannot facilitate unsolicited discovery.</span>
                <span lang="de"><b>Discovery-Policy-Durchsetzung (v25.3.1):</b> Konten sind standardmäßig in der Suche verborgen. Das Hinzufügen eines Kontakts erfordert eine Einladungsanfrage mit gegenseitiger Zustimmung, die der Empfänger annehmen oder ablehnen kann. Das Relay pflegt keinen sozialen Graphen und kann keine ungebetene Entdeckung ermöglichen.</span>
            </li>
            <li>
                <span lang="en"><b>Payload Opacity:</b> Message and attachment payloads are encrypted end-to-end; the relay cannot decrypt them. Server-side fields needed for routing are encrypted at rest with AES-256-GCM using <code>GHOST_FIELD_KEY</code>. The relay is not given plaintext sender or recipient content.</span>
                <span lang="de"><b>Payload-Opazität:</b> Nachrichten- und Anhangs-Payloads sind Ende-zu-Ende-verschlüsselt; das Relay kann sie nicht entschlüsseln. Serverseitige Felder, die für das Routing benötigt werden, sind mit AES-256-GCM unter Verwendung von <code>GHOST_FIELD_KEY</code> verschlüsselt. Dem Relay werden keine Klartext-Inhalte von Absender oder Empfänger übermittelt.</span>
            </li>
            <li>
                <span lang="en"><b>Identity Propagation (Inside-Ratchet):</b> Identity updates (avatars, usernames) are transmitted inside the Signal Double Ratchet. Because they are encrypted like other payloads, the relay cannot read them.</span>
                <span lang="de"><b>Identitäts-Propagation (Inside-Ratchet):</b> Identitätsaktualisierungen (Avatare, Benutzernamen) werden innerhalb des Signal-Double-Ratchet übertragen. Da sie wie andere Payloads verschlüsselt sind, kann das Relay sie nicht lesen.</span>
            </li>
            <li>
                <span lang="en"><b>Volatile Handshaking:</b> Signal "Noise" and heartbeat packets are handled in-memory and are not written to persistent storage, reducing the data footprint of connection attempts.</span>
                <span lang="de"><b>Flüchtiges Handshaking:</b> Signal-„Noise“- und Herzschlag-Pakete werden im Speicher verarbeitet und nicht in den persistenten Speicher geschrieben, was die Datenrückstände von Verbindungsversuchen verringert.</span>
            </li>
        </ul>

        <h3>2.2 <span lang="en">Transport-Layer Security (TLS) vs. E2EE</span><span lang="de">2.2 Transport-Layer Security (TLS) vs. E2EE</span></h3>
        <p>
            <span lang="en">While TLS protects the data in transit from external interceptors, StateZer0 treats the relay itself as a potential adversary. The Signal Protocol (Double Ratchet) is used to wrap every payload, ensuring that even if the relay were compromised, the data remains cryptographically inaccessible.</span>
            <span lang="de">Während TLS die Daten während der Übertragung vor externen Interzeptoren schützt, betrachtet StateZer0 das Relay selbst als potenziellen Angreifer. Das Signal-Protokoll (Double Ratchet) wird verwendet, um jede Payload zu umhüllen, wodurch sichergestellt wird, dass die Daten selbst bei einer Kompromittierung des Relays kryptografisch unzugänglich bleiben.</span>
        </p>

        <h3>2.3 <span lang="en">Sovereign Identity Bridge (v53.2.0)</span><span lang="de">2.3 Souveräne Identitätsbrücke (v53.2.0)</span></h3>
        <p>
            <span lang="en">StateZer0 v53.2.0 implements the <b>Decentralized Identity Bridge</b>. Contact relationships are established through local peer-to-peer handshakes rather than a server-side contact registry. The migration from an anonymous routing identifier to a verified UUID occurs through local atomic transitions. An <b>Indexed Alias Proxy</b> (<i>contact_aliases</i>) preserves local history continuity without exposing user links to the relay.</span>
            <span lang="de">StateZer0 v53.2.0 implementiert die <b>Dezentrale Identitätsbrücke</b>. Kontaktbeziehungen werden über lokale Peer-to-Peer-Handshakes etabliert, nicht über ein serverseitiges Kontaktregister. Die Migration von einem anonymen Routing-Identifikator zu einer verifizierten UUID erfolgt über lokale atomare Übergänge. Ein <b>indizierter Alias-Proxy</b> (<i>contact_aliases</i>) erhält die lokale Historienkontinuität, ohne dem Relay Benutzerlinks preiszugeben.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Atomic Promotion Orchestration:</b> Database ID swaps, Signal ratchet re-binding, and message re-anchoring are executed as an indivisible unit. Any failure triggers an automatic state rollback.</span>
                <span lang="de"><b>Atomare Promotion-Orchestrierung:</b> Datenbank-ID-Swaps, Signal-Ratchet-Re-Binding und Nachrichten-Re-Anchoring werden als unteilbare Einheit ausgeführt. Jeder Fehler löst einen automatischen Status-Rollback aus.</span>
            </li>
            <li>
                <span lang="en"><b>Deterministic Tie-Breaking:</b> Handshake collisions (simultaneous adds) are resolved via Identity Key comparisons, converging both clients to the same session state without additional round-trips.</span>
                <span lang="de"><b>Deterministisches Tie-Breaking:</b> Handshake-Kollisionen (gleichzeitiges Hinzufügen) werden über Identitätsschlüsselvergleiche gelöst, wodurch beide Clients ohne zusätzliche Round-Trips in denselben Sitzungszustand überführt werden.</span>
            </li>
            <li>
                <span lang="en"><b>UI Identity Hot-Swap:</b> Active chat windows automatically re-skin to verified UUIDs in real-time, providing visual proof of identity promotion without session interruption.</span>
                <span lang="de"><b>UI Identity Hot-Swap:</b> Aktive Chat-Fenster werden in Echtzeit automatisch auf verifizierte UUIDs umgestellt, was einen visuellen Nachweis der Identitätsheraufstufung ohne Sitzungsunterbrechung liefert.</span>
            </li>
        </ul>

        <h3>2.4 <span lang="en">Protocol State Machine Guard (v36.0.0)</span><span lang="de">2.4 Protocol State Machine Guard (v36.0.0)</span></h3>
        <ul>
            <li>
                <span lang="en"><b>Sovereign QR Discovery (v25.1.4):</b> Implementation of a localized peer-to-peer discovery model. QR codes and <i>ghost://connect</i> URIs are generated and parsed locally, ensuring the relay remains blind to the discovery event. Visual payloads include the Public Identity Key (IK) for reliable out-of-band fingerprint verification.</span>
                <span lang="de"><b>Souveräne QR-Entdeckung (v25.1.4):</b> Implementierung eines lokalisierten Peer-to-Peer-Entdeckungsmodells. QR-Codes und <i>ghost://connect</i>-URIs werden lokal erzeugt und analysiert, wodurch sichergestellt wird, dass das Relay gegenüber dem Entdeckungsereignis blind bleibt. Visuelle Payloads enthalten den öffentlichen Identitätsschlüssel (IK) für eine zuverlässige Out-of-Band-Fingerabdruck-Verifizierung.</span>
            </li>
            <li>
                <span lang="en"><b>Adaptive Status Throttling (v25.1.4):</b> To preserve terminal battery and reduce infrastructure jitter, the client implements a Foreground-Aware Polling Engine. Refresh intervals are dynamically cooled to 60 seconds when in the background.</span>
                <span lang="de"><b>Adaptive Status-Drosselung (v25.1.4):</b> Um die Akkulaufzeit des Endgeräts zu verlängern und Infrastruktur-Jitter zu reduzieren, implementiert der Client eine Foreground-Aware-Polling-Engine. Die Aktualisierungsintervalle werden im Hintergrund dynamisch auf 60 Sekunden abgekühlt.</span>
            </li>
            <li>
                <span lang="en"><b>Sovereign Short-Codes:</b> UUIDs are replaced with 6-character alphanumeric codes (Base32), offering about $1.07 \times 10^9$ combinations. This makes guessing a specific code practically infeasible.</span>
                <span lang="de"><b>Sovereign Short-Codes:</b> UUIDs werden durch 6-stellige alphanumerische Codes (Base32) mit etwa $1,07 \times 10^9$ Kombinationen ersetzt. Damit ist das Erraten eines bestimmten Codes praktisch unmöglich.</span>
            </li>
            <li>
                <span lang="en"><b>Large Payload Support:</b> Encrypted attachments (videos/documents) are limited to 100 MB, with a 25 MB optimization trigger.</span>
                <span lang="de"><b>Große Payload-Unterstützung:</b> Verschlüsselte Anhänge (Videos/Dokumente) sind auf 100 MB begrenzt, mit einem Optimierungstrigger bei 25 MB.</span>
            </li>
            <li>
                <span lang="en"><b>Autonomous Key Recovery:</b> The signature engine automatically fail-overs to an ephemeral <b>secp256r1</b> key pair if environment variables are mangled, ensuring compatibility across restricted OpenJDK/Render environments.</span>
                <span lang="de"><b>Autonome Schlüsselwiederherstellung:</b> Die Signatur-Engine führt automatisch ein Failover auf ein ephemeres <b>secp256r1</b>-Schlüsselpaar durch, falls Umgebungsvariablen beschädigt sind, um die Kompatibilität in eingeschränkten OpenJDK/Render-Umgebungen zu gewährleisten.</span>
            </li>
            <li>
                <span lang="en"><b>Beta Identity Re-rolling:</b> Authorized testers can re-register new identities on previously occupied hardware using a <b>GHOST_BETA_TESTER</b> token. The server purges the previous device-bound record automatically, avoiding manual database edits.</span>
                <span lang="de"><b>Beta-Identitäts-Re-rolling:</b> Autorisierte Tester können mit einem <b>GHOST_BETA_TESTER</b>-Token neue Identitäten auf bereits belegter Hardware neu registrieren. Der Server bereinigt den vorherigen gerätegebundenen Datensatz automatisch, ohne manuelle Datenbankeingriffe.</span>
            </li>
            <li>
                <span lang="en"><b>Transactional Relay Mutex (v25.1.2):</b> Implemented a localized <i>relayMutex</i> to enforce strict registration atomicity for multi-attachment bundles. This prevents race conditions and redundant network submissions (Triple-Delivery Mitigation) during parallel background uploads.</span>
                <span lang="de"><b>Transaktionales Relay-Mutex (v25.1.2):</b> Implementierung eines lokalisierten <i>relayMutex</i>, um eine strikte Registrierungs-Atomizität für Multi-Attachment-Bundles zu erzwenen. Dies verhindert Race-Conditions und redundante Netzwerkübermittlungen (Triple-Delivery Mitigation) während paralleler Hintergrund-Uploads.</span>
            </li>
        </ul>

        <h2><span lang="en">III. Client-Side Cryptographic Core (Deep Dive)</span><span lang="de">III. Clientseitiger kryptografischer Kern (Deep Dive)</span></h2>

        <h3>3.1 <span lang="en">Identity & Device-Bound Scarcity (The 1-Device Rule)</span><span lang="de">3.1 Identität & gerätegebundene Knappheit (Die 1-Geräte-Regel)</span></h3>
        <p>
            <span lang="en">To enforce account scarcity and limit automated Sybil attacks, StateZer0 ties each account to a device-bound identity key.</span>
            <span lang="de">Um Kontenknappheit durchzusetzen und automatisierte Sybil-Angriffe einzuschränken, bindet StateZer0 jedes Konto an einen gerätegebundenen Identitätsschlüssel.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Android Keystore Identity Key:</b> The client generates a device-bound identity key in <b>Android Keystore</b>. The key is non-exportable and used to derive a stable device identifier that the server checks for scarcity enforcement.</span>
                <span lang="de"><b>Android-Keystore-Identitätsschlüssel:</b> Der Client generiert einen gerätegebundenen Identitätsschlüssel im <b>Android Keystore</b>. Der Schlüssel ist nicht exportierbar und dient zur Ableitung eines stabilen Geräte-Identifikators, den der Server auf Knappheit prüft.</span>
            </li>
            <li>
                <span lang="en"><b>BETA BYPASS (Temporary):</b> In debug builds, the <b>One-Device Rule</b> can be bypassed for authorized beta testers using a <b>GHOST_BETA_TESTER</b> token. The relay deletes the previous device-bound record so testers can re-register on the same hardware. This logic is not present in release builds.</span>
                <span lang="de"><b>BETA-BYPASS (Temporär):</b> In Debug-Builds kann die <b>Ein-Gerät-Regel</b> für autorisierte Beta-Tester mit einem <b>GHOST_BETA_TESTER</b>-Token umgangen werden. Das Relay löscht den vorherigen gerätegebundenen Datensatz, sodass Tester sich auf derselben Hardware neu registrieren können. Diese Logik ist in Release-Builds nicht enthalten.</span>
            </li>
            <li>
                <span lang="en"><b>Device Attestation:</b> The registration flow invokes the <b>Google Play Integrity API</b> to obtain a token used as an integrity signal. The relay rejects attempts to register a device-bound identifier that is already marked as occupied.</span>
                <span lang="de"><b>Geräte-Attestierung:</b> Der Registrierungsablauf ruft die <b>Google Play Integrity API</b> auf, um ein Token als Integritätssignal zu erhalten. Das Relay lehnt Versuche ab, einen bereits als belegt markierten gerätegebundenen Identifikator erneut zu registrieren.</span>
            </li>
            <li>
                <span lang="en"><b>Backup Anchor:</b> An identity marker is stored through the configured Android backup mechanism (via <b>backup_rules.xml</b>). A re-installed application can detect prior occupancy and require the 12-word recovery flow.</span>
                <span lang="de"><b>Backup-Anker:</b> Ein Identitätsmarker wird über den konfigurierten Android-Backup-Mechanismus (via <b>backup_rules.xml</b>) gespeichert. Eine neu installierte Anwendung kann eine vorherige Belegung erkennen und den 12-Wörter-Wiederherstellungsablauf erzwingen.</span>
            </li>
        </ul>

        <h3>3.2 <span lang="en">Session Initialization (X3DH)</span><span lang="de">3.2 Sitzungs-Initialisierung (X3DH)</span></h3>
        <p>
            <span lang="en">StateZer0 implements the Extended Triple Diffie-Hellman (X3DH) key agreement protocol to establish a shared secret between mutually untrusted parties.</span>
            <span lang="de">StateZer0 implementiert das Extended Triple Diffie-Hellman (X3DH) Key-Agreement-Protokoll, um ein gemeinsames Geheimnis zwischen gegenseitig nicht vertrauenswürdigen Parteien zu etablieren.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Identity Keys (IK):</b> Long-term Curve25519 key pair.</span>
                <span lang="de"><b>Identity Keys (IK):</b> Langfristiges Curve25519-Schlüsselpaar.</span>
            </li>
            <li>
                <span lang="en"><b>Signed PreKeys (SPK):</b> Rotated every 48 hours (via SignalKeyManager.performKeyMaintenance()) to ensure forward secrecy.</span>
                <span lang="de"><b>Signed PreKeys (SPK):</b> Werden alle 48 Stunden rotiert (via SignalKeyManager.performKeyMaintenance()), um Forward Secrecy zu gewährleisten.</span>
            </li>
            <li>
                <span lang="en"><b>One-Time PreKeys (OPK):</b> A batch of 80 ephemeral keys is replenished automatically, allowing E2EE initialization for offline recipients once they come back online.</span>
                <span lang="de"><b>One-Time PreKeys (OPK):</b> Ein Batch von 80 ephemeren Schlüsseln wird automatisch aufgefüllt, um eine E2EE-Initialisierung für Offline-Empfänger zu ermöglichen, sobald diese wieder online sind.</span>
            </li>
        </ul>

        <h3>3.2 <span lang="en">The Double Ratchet Mechanism</span><span lang="de">3.2 Der Double-Ratchet-Mechanismus</span></h3>
        <p>
            <span lang="en">Payload encryption is managed by the Double Ratchet mechanism, combining a Diffie-Hellman (DH) Ratchet and a Symmetric-Key Ratchet.</span>
            <span lang="de">Die Verschlüsselung der Payload wird durch den Double-Ratchet-Mechanismus verwaltet, der einen Diffie-Hellman (DH) Ratchet und einen Symmetric-Key Ratchet kombiniert.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Perfect Forward Secrecy (PFS):</b> Every message is encrypted with a unique key derived from the rolling ratchet. Compromising one key yields no access to previous messages.</span>
                <span lang="de"><b>Perfect Forward Secrecy (PFS):</b> Jede Nachricht wird mit einem eindeutigen Schlüssel verschlüsselt, der aus dem rotierenden Ratchet abgeleitet wird. Die Kompromittierung eines Schlüssels ermöglicht keinen Zugriff auf vorherige Nachrichten.</span>
            </li>
            <li>
                <span lang="en"><b>Break-in Recovery (Future Secrecy):</b> If an adversary compromises a device's current state, the DH ratchet ensures the session "heals" as soon as the next message exchange occurs, locking the adversary out of future communications.</span>
                <span lang="de"><b>Break-in Recovery (Future Secrecy):</b> Wenn ein Angreifer den aktuellen Zustand eines Geräts kompromittiert, stellt der DH-Ratchet sicher, dass die Sitzung „heilt“, sobald der nächste Nachrichtenaustausch stattfindet, wodurch der Angreifer von der zukünftigen Kommunikation ausgeschlossen wird.</span>
            </li>
        </ul>

        <h3>3.3 <span lang="en">Deterministic Identity & BIP39 Restorations</span><span lang="de">3.3 Deterministische Identität & BIP39-Wiederherstellungen</span></h3>
        <p>
            <span lang="en">StateZer0 derives the master identity keypair from the 12-word BIP39 mnemonic. This avoids "Identity Changed" warnings when the same mnemonic is restored on a new device.</span>
            <span lang="de">StateZer0 leitet das Master-Identitätsschlüsselpaar aus dem 12-Wörter-BIP39-Mnemonic ab. Dadurch werden Warnungen über eine „geänderte Identität“ vermieden, wenn derselbe Mnemonic auf einem neuen Gerät wiederhergestellt wird.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Derivation Formula:</b> PBKDF2(HMAC-SHA256, Username + Mnemonic, Salt="GHOST_IDENTITY...", Iterations=4096).</span>
                <span lang="de"><b>Ableitungsformel:</b> PBKDF2(HMAC-SHA256, Username + Mnemonic, Salt=„GHOST_IDENTITY...“, Iterationen=4096).</span>
            </li>
            <li>
                <span lang="en"><b>Security Impact:</b> This allows a user to restore their cryptographic identity or reset a forgotten password on any hardware without a cloud-based backup, maintaining sovereignty over their private keys.</span>
                <span lang="de"><b>Sicherheitsauswirkung:</b> Dies ermöglicht es einem Benutzer, seine kryptografische Identität wiederherzustellen oder ein vergessenes Passwort auf jeder Hardware ohne Cloud-basiertes Backup zurückzusetzen, wodurch die Souveränität über seine privaten Schlüssel erhalten bleibt.</span>
            </li>
        </ul>

        <h3>3.4 <span lang="en">Local Storage Encryption & Binary Hardening</span><span lang="de">3.4 Lokale Speicherverschlüsselung & Binäre Härtung</span></h3>
        <p>
            <span lang="en">Data-at-rest is protected via SQLCipher (AES-256), complemented by binary hardening protocols.</span>
            <span lang="de">Ruhende Daten (Data-at-rest) werden über SQLCipher (AES-256) geschützt, ergänzt durch Binär-Härtungsprotokolle.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Android Keystore Key Wrapping:</b> The database passphrase is wrapped using an AES-GCM key stored in <b>Android Keystore</b>. This increases the difficulty of extracting the passphrase from a memory dump, but does not make extraction impossible.</span>
                <span lang="de"><b>Android-Keystore-Key-Wrapping:</b> Die Datenbank-Passphrase wird mit einem AES-GCM-Schlüssel umhüllt, der im <b>Android Keystore</b> gespeichert ist. Dies erschwert das Extrahieren der Passphrase aus einem Speicher-Dump, macht es aber nicht unmöglich.</span>
            </li>
            <li>
                <span lang="en"><b>Binary Execution Hardening (16 KB Alignment):</b> Native libraries are kept uncompressed and 16 KB page-aligned inside the APK to satisfy Android 15+ mapping requirements.</span>
                <span lang="de"><b>Binäre Ausführungshärtung (16 KB Alignment):</b> Native Bibliotheken bleiben unkomprimiert und mit 16 KB Seitenalignment im APK, um die Anforderungen von Android 15+ zu erfüllen.</span>
            </li>
        </ul>

        <h3>3.5 <span lang="en">Memory Space Hardening (RAM Sanitization)</span><span lang="de">3.5 Speicherhärtung (RAM-Sanitisation)</span></h3>
        <p>
            <span lang="en">To mitigate "Heap Allocation Leaks," StateZer0 enforces strict RAM hygiene:</span>
            <span lang="de">Um „Heap Allocation Leaks“ zu minimieren, erzwingt StateZer0 eine strikte RAM-Hygiene:</span>
        </p>
        <ul>
            <li>
                <span lang="en">Sensitive keys and mnemonics are handled as ByteArray or CharArray.</span>
                <span lang="de">Sensible Schlüssel und Mnemonics werden als ByteArray oder CharArray verarbeitet.</span>
            </li>
            <li>
                <span lang="en">In the finally block of every cryptographic operation (e.g., MnemonicUtils.generateSeed), the memory is zeroed out using Arrays.fill(key, 0).</span>
                <span lang="de">Im finally-Block jeder kryptografischen Operation (z. B. MnemonicUtils.generateSeed) wird der Speicher mit Arrays.fill(key, 0) auf Null gesetzt.</span>
            </li>
        </ul>

        <h2>IV. Sovereign Vault & Encrypted Media Pipeline</h2>

        <h3>4.1 <span lang="en">The Sovereign Vault (Encrypted Archive Management)</span><span lang="de">Der Sovereign Vault (Verschlüsselte Archivverwaltung)</span></h3>
        <p>
            <span lang="en">StateZer0 introduces the Sovereign Vault, a localized, encrypted repository for long-term storage of sensitive media and text. Unlike standard galleries, the Vault operates strictly within the "Ghost Protocol" parameters.</span>
            <span lang="de">StateZer0 führt den Sovereign Vault ein, ein lokales, verschlüsseltes Repository für die langfristige Speicherung sensibler Medien und Texte. Im Gegensatz zu Standardgalerien arbeitet der Vault streng innerhalb der „Ghost-Protokoll“-Parameter.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Proprietary .ghost Envelopes:</b> Assets are exported as encrypted blobs. These files are indexed via deterministic SHA-256 hashes; decryption keys are stored in the local SQLCipher database and are never sent to the server.</span>
                <span lang="de"><b>Proprietäre .ghost-Envelopes:</b> Assets werden als verschlüsselte Blobs exportiert. Diese Dateien werden über deterministische SHA-256-Hashes indiziert; Entschlüsselungsschlüssel werden in der lokalen SQLCipher-Datenbank gespeichert und niemals an den Server gesendet.</span>
            </li>
            <li>
                <span lang="en"><b>Metadata Sanitization (v25.1.0):</b> EXIF and other metadata (GPS coordinates, device make/model tags, capture timestamps) are stripped before encryption. This reduces, but cannot fully guarantee, the absence of location or device-related information in the encrypted blob.</span>
                <span lang="de"><b>Metadaten-Bereinigung (v25.1.0):</b> EXIF- und andere Metadaten (GPS-Koordinaten, Hersteller-/Modell-Tags, Aufnahmezeitstempel) werden vor der Verschlüsselung entfernt. Dies verringert, kann aber nicht vollständig garantieren, dass im verschlüsselten Blob keine standort- oder gerätebezogenen Informationen enthalten sind.</span>
            </li>
            <li>
                <span lang="en"><b>The Sovereign Transcript Seal (v11.0.0):</b> Text messages can be archived directly into the Vault, bypassing the system clipboard. The archived stream is encrypted; each record stores a provenance header (sender ID/timestamp) locally.</span>
                <span lang="de"><b>The Sovereign Transcript Seal (v11.0.0):</b> Textnachrichten können direkt in den Vault archiviert werden, wobei die Systemzwischenablage umgangen wird. Der archivierte Stream wird verschlüsselt; jeder Datensatz speichert lokal einen Provenienz-Header (Sender-ID/Zeitstempel).</span>
            </li>
            <li>
                <span lang="en"><b>Secure Reshare (v25.1.2):</b> Vaulted items reshared to contacts reuse the original encryption keys. No new plaintext copy of the file is created for reshare.</span>
                <span lang="de"><b>Sicheres Weiterteilen (v25.1.2):</b> Beim Weiterteilen von Vault-Elementen an Kontakte werden die ursprünglichen Verschlüsselungsschlüssel wiederverwendet. Für das Weiterteilen wird keine neue Klartextkopie der Datei erstellt.</span>
            </li>
            <li>
                <span lang="en"><b>Atomic Enclave Ingress (v40.1.6):</b> StateZer0 supports multi-attachment bundles. Multiple images, videos, or documents can be grouped into a single encrypted enclave. The platform uses an isolated staging area (<code>GHOST_STAGING_</code>) with UUID seeds; files are moved to the final payload namespace only after database confirmation.</span>
                <span lang="de"><b>Atomarer Enklaven-Ingress (v40.1.6):</b> StateZer0 unterstützt Multi-Attachment-Bundles. Mehrere Bilder, Videos oder Dokumente können in einer einzigen verschlüsselten Enklave gruppiert werden. Die Plattform nutzt einen isolierten Staging-Bereich (<code>GHOST_STAGING_</code>) mit UUID-Seeds; Dateien werden erst nach Datenbankbestätigung in den finalen Payload-Namensraum verschoben.</span>
            </li>
            <li>
                <span lang="en"><b>Enclave Playback Stabilization (v25.2.8):</b> The playback path uses hardware surface resets and alpha masking to reduce decoder contention. Media is decrypted into memory for playback; temporary buffers are released when playback ends.</span>
                <span lang="de"><b>Enklaven-Playback-Stabilisierung (v25.2.8):</b> Der Playback-Pfad verwendet Hardware-Oberflächen-Resets und Alpha-Masking, um Decoder-Konflikte zu reduzieren. Medien werden für die Wiedergabe in den Speicher entschlüsselt; temporäre Puffer werden nach Beendigung der Wiedergabe freigegeben.</span>
            </li>
            <li>
                <span lang="en"><b>Sovereign Enclave Swiping (v25.1.2):</b> Multi-media bundles are navigated via ViewPager2. Each item is decrypted into memory for viewing; decrypted buffers are released when the user swipes away.</span>
                <span lang="de"><b>Souveränes Enklaven-Swiping (v25.1.2):</b> Multimedia-Bundles werden über ViewPager2 navigiert. Jedes Element wird für die Anzeige in den Speicher entschlüsselt; entschlüsselte Puffer werden freigegeben, wenn der Benutzer wegwischt.</span>
            </li>
            <li>
                <span lang="en"><b>Static GIF Previews (v25.1.2):</b> GIFs are rendered as static placeholders in the chat history. Animation is triggered only by explicit user interaction, reducing background processing and flicker.</span>
                <span lang="de"><b>Statische GIF-Vorschauen (v25.1.2):</b> GIFs werden im Chat-Verlauf als statische Platzhalter gerendert. Die Animation wird nur durch explizite Benutzerinteraktion ausgelöst, was Hintergrundverarbeitung und Flackern reduziert.</span>
            </li>
            <li>
                <span lang="en"><b>Mixed Media Iterative Routing (v29.1.0):</b> StateZer0 uses an iterative routing engine for multi-attachment enclaves. Videos, images, and documents can be sent in one action; metadata is resolved independently per item and stored in a parent-child database relationship.</span>
                <span lang="de"><b>Mixed-Media Iteratives Routing (v29.1.0):</b> StateZer0 nutzt eine iterative Routing-Engine für Multi-Attachment-Enklaven. Videos, Bilder und Dokumente können in einer Aktion gesendet werden; Metadaten werden pro Element unabhängig aufgelöst und in einer Parent-Child-Datenbankbeziehung gespeichert.</span>
            </li>
            <li>
                <span lang="en"><b>Bundle Selection Menu:</b> The application provides a context-sensitive menu for bundles. Users can selectively save individual items to the Vault or Gallery.</span>
                <span lang="de"><b>Bundle-Auswahlmenü:</b> Die Anwendung bietet ein kontextsensitives Menü für Bundles. Benutzer können einzelne Elemente gezielt im Vault oder in der Galerie speichern.</span>
            </li>
            <li>
                <span lang="en"><b>Forced Player Release:</b> Active media players are released before a delete or account-wipe command runs, so file locks do not block deletion.</span>
                <span lang="de"><b>Forced Player Release:</b> Aktive Medienplayer werden freigegeben, bevor ein Lösch- oder Konto-Lösch-Befehl ausgeführt wird, damit Dateisperren die Löschung nicht blockieren.</span>
            </li>
            <li>
                <span lang="en"><b>Metadata Sterilization:</b> Every object added to the Vault has GPS tags, device signatures, and EXIF headers removed before encryption.</span>
                <span lang="de"><b>Metadaten-Sterilisation:</b> Jedem Objekt, das dem Vault hinzugefügt wird, werden GPS-Tags, Gerätesignaturen und EXIF-Header vor der Verschlüsselung entfernt.</span>
            </li>
            <li>
                <span lang="en"><b>Memory-Only Decryption:</b> Vault assets are decrypted into memory for viewing. No unencrypted persistent copy is kept; temporary cache files are cleared and overwritten as a best-effort measure.</span>
                <span lang="de"><b>Speicherbasierte Entschlüsselung:</b> Vault-Assets werden für die Anzeige in den Speicher entschlüsselt. Es wird keine unverschlüsselte persistente Kopie angelegt; temporäre Cache-Dateien werden nach bestem Bemühen geleert und überschrieben.</span>
            </li>
            <li>
                <span lang="en"><b>One-Tap Secure Deletion:</b> Deleting from the Vault removes the file and overwrites the storage area as a best-effort measure before deletion.</span>
                <span lang="de"><b>One-Tap Sichere Löschung:</b> Das Löschen aus dem Vault entfernt die Datei und überschreibt den Speicherbereich vor der Löschung nach bestem Bemühen.</span>
            </li>
        </ul>

        <h3>4.2 <span lang="en">Ephemeral Symmetric Media Keys</span><span lang="de">4.2 Ephemere symmetrische Media-Keys</span></h3>
        <p>
            <span lang="en">High-overhead attachments (videos, images, documents) are encrypted using a Hybrid Blob Architecture:</span>
            <span lang="de">Attachments mit hohem Overhead (Videos, Bilder, Dokumente) werden mittels einer Hybrid-Blob-Architektur verschlüsselt:</span>
        </p>
        <ul>
            <li>
                <span lang="en">1. The client generates a unique 256-bit AES symmetric key for the specific file.</span>
                <span lang="de">1. Der Client generiert einen eindeutigen symmetrischen 256-Bit AES-Schlüssel für die spezifische Datei.</span>
            </li>
            <li>
                <span lang="en">2. The file is encrypted locally.</span>
                <span lang="de">2. Die Datei wird lokal verschlüsselt.</span>
            </li>
            <li>
                <span lang="en">3. The encrypted binary is uploaded to an untrusted storage provider (Cloudflare R2).</span>
                <span lang="de">3. Das verschlüsselte Binary wird zu einem nicht vertrauenswürdigen Speicheranbieter (Cloudflare R2) hochgeladen.</span>
            </li>
            <li>
                <span lang="en">4. The symmetric key and URL are sealed inside the Signal E2EE envelope and sent to the recipient.</span>
                <span lang="de">4. Der symmetrische Schlüssel und die URL werden im Signal-E2EE-Umschlag versiegelt und an den Empfänger gesendet.</span>
            </li>
        </ul>

        <h3>4.2 <span lang="en">Metadata Sterilization (EXIF &amp; Metadata Removal)</span><span lang="de">4.2 Metadaten-Sterilisation (EXIF- &amp; Metadaten-Entfernung)</span></h3>
        <p>
            <span lang="en">Before encryption, captured media items are processed by the MetadataStripper to remove identifying metadata.</span>
            <span lang="de">Vor der Verschlüsselung werden aufgenommene Medienobjekte vom MetadataStripper verarbeitet, um identifizierende Metadaten zu entfernen.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Metadata Overwrite:</b> The JPEG/MP4 header is parsed, and GPS tags, device signatures (model/make), and timestamps are overwritten or cleared.</span>
                <span lang="de"><b>Metadaten-Überschreibung:</b> Der JPEG/MP4-Header wird analysiert, und GPS-Tags, Gerätesignaturen (Modell/Marke) sowie Zeitstempel werden überschrieben oder gelöscht.</span>
            </li>
            <li>
                <span lang="en"><b>Privacy Impact:</b> This reduces the amount of location and device information carried by a photo or video shared with a recipient. It does not guarantee that all identifying metadata is removed.</span>
                <span lang="de"><b>Datenschutzauswirkung:</b> Dies verringert die Menge an Standort- und Geräteinformationen, die ein Foto oder Video an einen Empfänger weitergeben. Es garantiert nicht, dass alle identifizierenden Metadaten entfernt werden.</span>
            </li>
        </ul>

        <h3>4.3 <span lang="en">Volatile RAM & Secure Staging</span><span lang="de">4.3 Flüchtige RAM- & Sichere Staging-Schicht</span></h3>
        <p>
            <span lang="en">StateZer0 minimizes the footprint of unencrypted data. For images, documents, and audio, the platform uses a <b>Direct RAM Pipeline</b> that keeps unencrypted bytes in volatile memory where feasible. For videos requiring optimization, the system uses a temporary <b>Secure Staging Area</b>; temporary cache files are cleared and overwritten as a best-effort measure.</span>
            <span lang="de">StateZer0 minimiert die Menge unverschlüsselter Daten. Für Bilder, Dokumente und Audio nutzt die Plattform eine <b>Direct RAM Pipeline</b>, die unverschlüsselte Bytes nach Möglichkeit im flüchtigen Speicher hält. Für Videos, die eine Optimierung erfordern, nutzt das System einen temporären <b>Sicheren Staging-Bereich</b>; temporäre Cache-Dateien werden nach bestem Bemühen geleert und überschrieben.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Memory-Based Images/Audio:</b> Optimization and encryption of images and voice recordings occur in volatile memory buffers where the media pipeline supports it.</span>
                <span lang="de"><b>Speicherbasierte Bilder/Audio:</b> Optimierung und Verschlüsselung von Bildern und Sprachaufnahmen erfolgen in flüchtigen Speicherpuffern, soweit die Medien-Pipeline dies unterstützt.</span>
            </li>
            <li>
                <span lang="en"><b>Best-effort deletion:</b> Transient artifacts created during video transcoding are overwritten before deletion, reducing the chance of recovery.</span>
                <span lang="de"><b>Löschung nach bestem Bemühen:</b> Temporäre Artefakte, die während der Videotranskodierung entstehen, werden vor der Löschung überschrieben, um die Wiederherstellungswahrscheinlichkeit zu verringern.</span>
            </li>
            <li>
                <span lang="en"><b>Save Plain:</b> When a user saves a file to their gallery, the stream is decrypted into a volatile RAM buffer and passed directly to the MediaStore API.</span>
                <span lang="de"><b>Save Plain:</b> Wenn ein Benutzer eine Datei in seiner Galerie speichert, wird der Stream in einem flüchtigen RAM-Puffer entschlüsselt und direkt an die MediaStore-API geleitet.</span>
            </li>
            <li>
                <span lang="en"><b>Audio Sandbox:</b> Voice messages are recorded and decrypted in memory; buffers are zeroed after the MediaPlayer is released.</span>
                <span lang="de"><b>Audio-Sandbox:</b> Sprachnachrichten werden im Speicher aufgenommen und entschlüsselt; Puffer werden nach Freigabe des MediaPlayers mit Nullen gefüllt.</span>
            </li>
        </ul>

        <h2><span lang="en">V. Fault-Tolerant Self-Healing Mechanics (The Stability Engine)</span><span lang="de">V. Fehlertolerante Self-Healing-Mechanik (Die Stabilitäts-Engine)</span></h2>

        <h3>5.1 <span lang="en">Account Deletion (Scorched Earth / Panic PIN)</span><span lang="de">5.1 Kontolöschung (Scorched Earth / Panic PIN)</span></h3>
        <p>
            <span lang="en">Account deletion can be triggered through the Scorched Earth or Panic PIN flow. It removes server-side account data and performs a local wipe.</span>
            <span lang="de">Die Kontolöschung kann über den Scorched-Earth- oder Panic-PIN-Flow ausgelöst werden. Sie entfernt serverseitige Kontodaten und führt einen lokalen Wipe durch.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Server-side deletion:</b> <code>DELETE /users/me</code> removes the user row, pre-keys, sessions, push tokens, active invites, and undelivered messages and attachments.</span>
                <span lang="de"><b>Serverseitige Löschung:</b> <code>DELETE /users/me</code> entfernt die Benutzerzeile, Pre-Keys, Sitzungen, Push-Tokens, aktive Einladungen sowie unzugestellte Nachrichten und Anhänge.</span>
            </li>
            <li>
                <span lang="en"><b>Local wipe:</b> The local database, SharedPreferences, caches, and files are deleted, and running workers and notifications are cancelled. In Phase 1, the Android Keystore keys are left intact, but the encrypted database and wrapped passphrase files are destroyed, so the data is no longer recoverable through the app.</span>
                <span lang="de"><b>Lokaler Wipe:</b> Die lokale Datenbank, SharedPreferences, Caches und Dateien werden gelöscht und laufende Worker sowie Benachrichtigungen abgebrochen. In Phase 1 bleiben die Android-Keystore-Schlüssel erhalten, aber die verschlüsselte Datenbank und die umhüllten Passphrase-Dateien werden zerstört, sodass die Daten über die App nicht mehr wiederherstellbar sind.</span>
            </li>
            <li>
                <span lang="en"><b>Recovery note:</b> Because identity is derived from the 12-word BIP39 mnemonic, the same cryptographic identity can be restored later from the mnemonic. Prior local data will not be recoverable.</span>
                <span lang="de"><b>Wiederherstellungs-Hinweis:</b> Da die Identität vom 12-Wörter-BIP39-Mnemonic abgeleitet wird, kann dieselbe kryptografische Identität später aus dem Mnemonic wiederhergestellt werden. Vorherige lokale Daten sind nicht wiederherstellbar.</span>
            </li>
        </ul>

        <h3>5.2 <span lang="en">Hybrid AEC & Telecom Integration (VoIP)</span><span lang="de">5.2 Hybrid-AEC & Telecom-Integration (VoIP)</span></h3>
        <p>
            <span lang="en">StateZer0 uses the Android Telecom framework and hybrid echo cancellation to improve call stability.</span>
            <span lang="de">StateZer0 nutzt das Android-Telecom-Framework und hybride Echokompensation, um die Anrufstabilität zu verbessern.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Telecom Framework Integration:</b> A Self-Managed ConnectionService is used to request audio focus and background execution priority during calls.</span>
                <span lang="de"><b>Telecom-Framework-Integration:</b> Ein Self-Managed ConnectionService wird genutzt, um Audiofokus und Hintergrundausführungspriorität während Anrufen anzufordern.</span>
            </li>
            <li>
                <span lang="en"><b>Hybrid AEC & Volume Boost:</b> Acoustic Echo Cancellation is handled by hardware platform filters and a software-based adaptive filter (AEC3). A +150% digital gain stage is applied to improve speakerphone volume.</span>
                <span lang="de"><b>Hybrid-AEC & Volume Boost:</b> Die akustische Echokompensation wird von Hardware-Plattformfiltern und einem softwarebasierten adaptiven Filter (AEC3) verarbeitet. Eine +150%-digitale Gain-Stufe verbessert die Freisprechlautstärke.</span>
            </li>
            <li>
                <span lang="en"><b>Native Component Disposal (v52.0.0):</b> Native WebRTC components (AudioSource, AudioTrack, PeerConnection) receive explicit <code>dispose()</code> calls when a call ends. This releases native references and reduces the window in which sensitive data may remain in memory.</span>
                <span lang="de"><b>Freigabe nativer Komponenten (v52.0.0):</b> Native WebRTC-Komponenten (AudioSource, AudioTrack, PeerConnection) erhalten beim Beenden eines Anrufs explizite <code>dispose()</code>-Aufrufe. Dies gibt native Referenzen frei und verringert das Zeitfenster, in dem sensible Daten im Speicher verbleiben können.</span>
            </li>
            <li>
                <span lang="en"><b>TURN-Only Routing:</b> Calls are forced through TURN as a privacy choice. This hides peer IP addresses from each other but adds latency.</span>
                <span lang="de"><b>TURN-Only-Routing:</b> Anrufe werden als datenschutzorientierte Entscheidung über TURN geleitet. Dies verbirgt die Peer-IP-Adressen voreinander, erhöht aber die Latenz.</span>
            </li>
        </ul>

        <h3>5.2 <span lang="en">Silent Decryption Recovery</span><span lang="de">5.2 Stille Entschlüsselungs-Wiederherstellung</span></h3>
        <p>
            <span lang="en">SignalMessageManager implements a silent recovery path for ratchet desynchronizations (e.g., after long inactivity or storage corruption).</span>
            <span lang="de">Der SignalMessageManager implementiert einen stillen Wiederherstellungspfad für Ratchet-Desynchronisationen (z. B. nach langer Inaktivität oder Speicherbeschädigung).</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Background Handshake:</b> If a DuplicateMessageException or decryption error is detected, the app triggers an IDENTITY_RESET handshake in the background, without interrupting the UI.</span>
                <span lang="de"><b>Hintergrund-Handshake:</b> Wenn eine DuplicateMessageException oder ein Entschlüsselungsfehler erkannt wird, löst die App im Hintergrund einen IDENTITY_RESET-Handshake aus, ohne die Benutzeroberfläche zu unterbrechen.</span>
            </li>
        </ul>

        <h3>5.2 <span lang="en">Protocol Guard & Mutual Consent (v36.0.0)</span><span lang="de">5.2 Protocol Guard & Gegenseitige Zustimmung (v36.0.0)</span></h3>
        <p>
            <span lang="en">Incoming signals from unknown IDs are quarantined until the recipient explicitly accepts the invite request. Adding a contact requires a mutual-consent invite with Accept/Reject options; no ratchet handshake is committed automatically. The relay does not maintain a social graph.</span>
            <span lang="de">Eingehende Signale unbekannter IDs werden unter Quarantäne gestellt, bis der Empfänger die Einladungsanfrage explizit annimmt. Das Hinzufügen eines Kontakts erfordert eine Einladung mit gegenseitiger Zustimmung und den Optionen Annehmen/Ablehnen; kein Ratchet-Handshake wird automatisch festgeschrieben. Das Relay pflegt keinen sozialen Graphen.</span>
        </p>

        <h2><span lang="en">VI. Sovereign Multi-Device Migration Model</span><span lang="de">VI. Souveränes Multi-Device-Migrationsmodell</span></h2>

        <h3>6.1 <span lang="en">Single-Seat Identity Handoff</span><span lang="de">6.1 Single-Seat Identitätsübergabe</span></h3>
        <p>
            <span lang="en">StateZer0 enforces single-seat use during device migration: the old device is revoked before the new one becomes active.</span>
            <span lang="de">StateZer0 erzwingt während der Gerätemigration einen Single-Seat-Betrieb: Das alte Gerät wird widerrufen, bevor das neue aktiv wird.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Remote Session Revocation:</b> After authentication on device B (new), a <b>SYSTEM_DEVICE_REVOKE</b> signal is sent. The relay closes device A's WebSocket and invalidates its push token.</span>
                <span lang="de"><b>Remote-Sitzungswiderruf:</b> Nach der Authentifizierung auf Gerät B (neu) wird ein <b>SYSTEM_DEVICE_REVOKE</b>-Signal gesendet. Das Relay schließt den WebSocket von Gerät A und entwertet dessen Push-Token.</span>
            </li>
            <li>
                <span lang="en"><b>Local P2P Wi-Fi Bridge:</b> Database migration (messages, settings, profiles) happens over a direct local encrypted tunnel, avoiding third-party cloud storage. The tunnel is encrypted, but local Wi-Fi metadata (e.g., MAC addresses, SSID) is outside the app's control.</span>
                <span lang="de"><b>Lokale P2P-Wi-Fi-Brücke:</b> Die Datenbankmigration (Nachrichten, Einstellungen, Profile) erfolgt über einen direkten lokalen verschlüsselten Tunnel, ohne Cloud-Speicher Dritter. Der Tunnel ist verschlüsselt, lokale Wi-Fi-Metadaten (z. B. MAC-Adressen, SSID) unterliegen jedoch nicht der Kontrolle der App.</span>
            </li>
            <li>
                <span lang="en"><b>Best-Effort Deletion on the Old Device:</b> Device A triggers the <b>Scorched Earth</b> protocol only after device B confirms the migrated vault is usable. The wipe deletes local data as a best-effort measure; it does not guarantee that no recoverable traces remain.</span>
                <span lang="de"><b>Löschung auf dem alten Gerät nach bestem Bemühen:</b> Gerät A löst das <b>Scorched Earth</b>-Protokoll erst aus, nachdem Gerät B bestätigt hat, dass der migrierte Tresor nutzbar ist. Der Wipe entfernt lokale Daten nach bestem Bemühen; er garantiert nicht, dass keine wiederherstellbaren Rückstände verbleiben.</span>
            </li>
        </ul>

        <h2><span lang="en">VII. Infrastructure, Scalability, & Retention TTL</span><span lang="de">VII. Infrastruktur, Skalierbarkeit & Aufbewahrungs-TTL</span></h2>

        <h3>7.1 <span lang="en">Dependency & Licensing Compliance</span><span lang="de">7.1 Abhängigkeiten & Lizenz-Compliance</span></h3>
        <p>
            <span lang="en">Die Plattform nutzt Industriestandard-Bibliotheken, die kommerziell nutzbar sind:</span>
            <span lang="de">Die Plattform nutzt Industriestandard-Bibliotheken, die kommerziell nutzbar sind:</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Signal Protocol:</b> libsignal-android (GPLv3/kommerzielle kompatible Implementierung).</span>
                <span lang="de"><b>Signal-Protokoll:</b> libsignal-android (GPLv3/kommerzielle kompatible Implementierung).</span>
            </li>
            <li>
                <span lang="en"><b>Persistence:</b> Room + SQLCipher (BSD/Apache 2.0).</span>
                <span lang="de"><b>Persistenz:</b> Room + SQLCipher (BSD/Apache 2.0).</span>
            </li>
            <li>
                <span lang="en"><b>Concurrency:</b> Kotlin Coroutines & Flow.</span>
                <span lang="de"><b>Konkurrenz:</b> Kotlin Coroutines & Flow.</span>
            </li>
        </ul>

        <h3>7.2 <span lang="en">Retention & Time-to-Live (TTL)</span><span lang="de">7.2 Aufbewahrung & Time-to-Live (TTL)</span></h3>
        <p>
            <span lang="en">StateZer0 applies the following retention rules on the relay: delivered messages and attachments are erased within 24 hours (or 24 hours after acknowledgement); undelivered content is erased within 72 hours. The R2 reaper runs approximately every 10 minutes. Minimal server logs are retained for up to 30 days for abuse prevention and legal compliance. Local chat history remains on the user's device until deleted by the user or by a wipe.</span>
            <span lang="de">StateZer0 wendet folgende Aufbewahrungsregeln auf dem Relay an: Zugestellte Nachrichten und Anhänge werden innerhalb von 24 Stunden (oder 24 Stunden nach Bestätigung) gelöscht; unzugestellte Inhalte werden innerhalb von 72 Stunden gelöscht. Der R2-Reaper läuft etwa alle 10 Minuten. Minimale Server-Logs werden bis zu 30 Tage zur Missbrauchsprävention und Rechts compliance aufbewahrt. Die lokale Chathistorie verbleibt auf dem Gerät des Benutzers, bis der Benutzer sie löscht oder ein Wipe erfolgt.</span>
        </p>

        <h3>7.3 <span lang="en">Universal I18N & UX Standards (v25.4.0)</span><span lang="de">Universelle I18N & UX-Standards (v25.4.0)</span></h3>
        <p>
            <span lang="en">StateZer0 implements a 21-language localization framework using the Android Resources system.</span>
            <span lang="de">StateZer0 implementiert ein 21-Sprachen-Lokalisierungs-Framework über das Android-Ressourcensystem.</span>
        </p>
        <ul>
            <li>
                <span lang="en"><b>Alphabetical Endonym Collation:</b> To reduce user search friction, language selection listings are sorted alphabetically by their <b>Native Display Names</b> (Endonyms). This satisfies global accessibility standards and ensures intuitive navigation for multi-lingual users.</span>
                <span lang="de"><b>Alphabetische Endonym-Kollatierung:</b> Zur Reduzierung der Benutzer-Suchreibung werden die Sprachauswahllisten alphabetisch nach ihren <b>nativen Anzeigenamen</b> (Endonymen) sortiert. Dies erfüllt globale Barrierefreiheitsstandards und gewährleistet eine intuitive Navigation für mehrsprachige Benutzer.</span>
            </li>
            <li>
                <span lang="en"><b>No Hardcoded Strings:</b> UI components, including security dialogs and error toasts, are managed via the Android Resources system, supporting the 21 locales.</span>
                <span lang="de"><b>Keine hartcodierten Strings:</b> UI-Komponenten, einschließlich Sicherheitsdialogen und Fehler-Toasts, werden über das Android-Ressourcensystem verwaltet und unterstützen die 21 Lokalisierungen.</span>
            </li>
        </ul>

        <h3>7.4 <span lang="en">Security Audit Results</span><span lang="de">Ergebnisse des Sicherheits-Audits</span></h3>
        <ul>
            <li>
                <span lang="en"><b>Data Leakage:</b> Message and attachment payloads are encrypted end-to-end; the relay does not receive plaintext content. Profile data sent inside the Signal ratchet is also unreadable to the relay.</span>
                <span lang="de"><b>Datenabfluss:</b> Nachrichten- und Anhangs-Payloads sind Ende-zu-Ende-verschlüsselt; das Relay erhält keine Klartextinhalte. Profildaten, die innerhalb des Signal-Ratchets gesendet werden, sind für das Relay ebenfalls nicht lesbar.</span>
            </li>
            <li>
                <span lang="en"><b>Data Remnants:</b> Server-side content is deleted according to the retention TTLs above. Local remnants depend on the device storage controller and file system; deletion is performed as a best-effort measure.</span>
                <span lang="de"><b>Datenüberreste:</b> Serverseitige Inhalte werden gemäß den obigen Aufbewahrungs-TTLs gelöscht. Lokale Rückstände hängen vom Gerätespeicher-Controller und Dateisystem ab; die Löschung erfolgt nach bestem Bemühen.</span>
            </li>
            <li>
                <span lang="en"><b>Protocol Resilience:</b> The implementation includes identity reset and network fragmentation handling. Effectiveness depends on deployment and client state.</span>
                <span lang="de"><b>Protokoll-Resilienz:</b> Die Implementierung enthält Handhabung für Identitäts-Resets und Netzwerkfragmentierung. Die Wirksamkeit hängt vom Betrieb und vom Client-Zustand ab.</span>
            </li>
        </ul>

        <div class="status-footer">
            Legal Compliance: EU DSGVO, GDPR Art. 11, German TDDDG § 25.<br>
            System Integrity: GHOST PROTOCOL v76.0.0-STABLE ACTIVE. dQuantumBear 🛡️🚀🐻❤️
        </div>
    </div>

    <script>
        function setLang(lang) {
            const supportedLangs = ['en', 'de'];
            const targetLang = supportedLangs.includes(lang) ? lang : 'en';
            document.documentElement.lang = targetLang;
            localStorage.setItem('preferred-lang', targetLang);
            updateButtons(targetLang);
        }

        function updateButtons(lang) {
            const btnEn = document.getElementById('btn-en');
            const btnDe = document.getElementById('btn-de');
            if (btnEn) btnEn.classList.toggle('active', lang === 'en');
            if (btnDe) btnDe.classList.toggle('active', lang === 'de');
        }

        // AI-FIX: Automatic Language Detection (v1.5.0)
        // Priority: 1. URL Param (?lang=) | 2. LocalStorage | 3. Browser Navigator | 4. Default (en)
        const urlParams = new URLSearchParams(window.location.search);
        const urlLang = urlParams.get('lang');
        const browserLang = navigator.language.split('-')[0];

        const savedLang = urlLang || localStorage.getItem('preferred-lang') || browserLang || 'en';
        setLang(savedLang);
    </script>
</body>
</html>

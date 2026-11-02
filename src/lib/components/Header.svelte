<script>
	// format von date-fns, um das heutige Datum schön zu zeigen
	import { format } from 'date-fns';
	// deutsche Sprache für Wochentag und Monat
	import { de } from 'date-fns/locale';

	// Props von der Seite: total = Anzahl Issues, onAdd und onExport = Funktionen für die Buttons
	let { total, onAdd, onExport } = $props();

	// heutiges Datum, z.B. "Montag, 2. November 2026"
	const today = format(new Date(), 'EEEE, d. MMMM yyyy', { locale: de });
</script>

<!-- Kopfzeile. flex justify-between = links Titel, rechts Buttons. flex-wrap = am Handy untereinander -->
<header class="mb-8 flex flex-wrap items-center justify-between gap-5 rounded-3xl border border-white/80 bg-white/75 px-6 py-6 shadow-[0_12px_40px_rgba(67,61,120,0.07)] backdrop-blur md:px-8">
	<!-- linke Seite: Datum, Titel, Anzahl -->
	<div>
		<p class="mb-1 text-sm text-ink-soft">{today}</p>
		<h1 class="font-sans text-4xl font-bold leading-none tracking-tight text-ink md:text-5xl">Kanban</h1>
		<p class="mt-2 text-sm text-ink-soft">{total} Issues auf dem Board</p>
	</div>

	<!-- rechte Seite: die zwei Buttons -->
	<div class="flex gap-2">
		<!-- CSV Export: ruft die Funktion onExport von der Seite auf -->
		<button
			class="cursor-pointer rounded-xl border border-line bg-white px-4 py-2.5 text-sm font-semibold shadow-sm hover:border-lane-do hover:bg-paper"
			onclick={onExport}
		>
			CSV Export
		</button>
		<!-- Neues Issue: ruft onAdd auf, das öffnet den Dialog -->
		<button
			class="cursor-pointer rounded-xl bg-lane-do px-5 py-2.5 text-sm font-semibold text-white shadow-md shadow-lane-do/20 hover:bg-ink"
			onclick={onAdd}
		>
			+ Neues Issue
		</button>
	</div>
</header>

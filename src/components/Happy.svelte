<h1 id="happy">Happy Birthday</h1>

<style>
	@font-face {
		font-family: 'Super Donuts';
		src: url('/fonts/super_donuts.ttf');
		/* src: local('Super Donuts'), url('$lib/fonts/super_donuts.ttf') format('ttf'); */
	}
	@font-face {
		font-family: 'Glakome';
		src: url('/fonts/glakome.otf');
	}

	#happy {
		font-family: 'Super Donuts';
		font-size: 3em;
		text-align: center;
		color: rgb(255, 200, 0);
		display: inline-block;
		vertical-align: middle;
		position: absolute;
		width: 200px;
		height: 200px;
	}

	/**
 * CSS for Super Donuts
 * Generated by Wakamai Fondue - https://wakamaifondue.com
 * by Roel Nieskens/PixelAmbacht - https://pixelambacht.nl
 */

	@font-face {
		font-family: 'Super Donuts';
		src: url('V5vhZm.ttfI.ttf');
		unicode-range: U+0000, U+000D, U+0020-007E, U+00A1-00AC, U+00AE-00B4, U+00B6-00FF, U+0110-0111,
			U+0131, U+0141-0142, U+0152-0153, U+0160-0161, U+0178, U+017D-017E, U+0192, U+02C6-02C7,
			U+02D8-02DD, U+03BC, U+2013-2014, U+2018-201A, U+201C-201E, U+2020-2022, U+2026, U+2030,
			U+2039-203A, U+2044, U+20AC, U+2122, U+2212, U+FB01-FB02;
	}

	/* Set custom properties for each layout feature */
	:root {
		--super-donuts-aalt: 'aalt' off;
		--super-donuts-frac: 'frac' off;
		--super-donuts-ordn: 'ordn' off;
		--super-donuts-sups: 'sups' off;
	}

	/* If class is applied, update custom property and
   apply modern font-variant-* when supported */
	.super-donuts-aalt {
		--super-donuts-aalt: 'aalt' on;
	}

	.super-donuts-frac {
		--super-donuts-frac: 'frac' on;
	}

	@supports (font-variant-numeric: diagonal-fractions) {
		.super-donuts-frac {
			--super-donuts-frac: '____';
			font-variant-numeric: diagonal-fractions;
		}
	}

	.super-donuts-ordn {
		--super-donuts-ordn: 'ordn' on;
	}

	@supports (font-variant-numeric: ordinal) {
		.super-donuts-ordn {
			--super-donuts-ordn: '____';
			font-variant-numeric: ordinal;
		}
	}

	.super-donuts-sups {
		--super-donuts-sups: 'sups' on;
	}

	@supports (font-variant-position: super) {
		.super-donuts-sups {
			--super-donuts-sups: '____';
			font-variant-position: super;
		}
	}

	/* Apply current state of all custom properties
   whenever a class is being applied */
	.super-donuts-aalt,
	.super-donuts-frac,
	.super-donuts-ordn,
	.super-donuts-sups {
		font-feature-settings: var(--super-donuts-aalt), var(--super-donuts-frac),
			var(--super-donuts-ordn), var(--super-donuts-sups);
	}
</style>

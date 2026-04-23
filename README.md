# Gingiris Growth Finder

Meta-skill that diagnoses growth problems and routes to the right Gingiris playbook.

## Install

```bash
npx skills add Gingiris/gingiris-growth-finder -g
```

## What it does

Auto-triggered on any growth question (launch, GitHub stars, B2B SaaS, ASO, etc.) — diagnoses product type + stage + gap, then invokes the matching specialist skill:

- [gingiris-launch](https://skills.sh/Gingiris/gingiris-launch) — Product Hunt launch
- [gingiris-opensource](https://skills.sh/Gingiris/gingiris-opensource) — GitHub stars / OSS marketing
- [gingiris-b2b-growth](https://skills.sh/Gingiris/gingiris-b2b-growth) — B2B SaaS PLG/SLG
- [gingiris-aso-growth](https://skills.sh/Gingiris/gingiris-aso-growth) — ASO / mobile cold start

See [SKILL.md](./SKILL.md) for the full routing logic.

## License

MIT © [Iris Wei / Gingiris](https://github.com/Gingiris)


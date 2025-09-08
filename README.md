# Call.Report Documentation Site

This repository contains the documentation website for Call.Report, providing open-source resources and code for analyzing bank regulatory data.

## 🚀 Quick Start

### Building the Documentation

1. **Install dependencies**:
```bash
pip install mkdocs mkdocs-material pymdown-extensions
```

2. **Serve locally for development**:
```bash
mkdocs serve
# Visit http://127.0.0.1:8000
```

3. **Build static site**:
```bash
mkdocs build
```

4. **Deploy to GitHub Pages**:
```bash
mkdocs gh-deploy --branch production
```

## 📁 Repository Structure

```
call-report.github.io/
├── docs/               # Source markdown files
│   ├── index.md       # Homepage
│   ├── code.md        # Code Library
│   ├── datalibrary.md # Data Library
│   └── ...
├── mkdocs.yml         # MkDocs configuration
├── CLAUDE.md          # AI assistant guidelines
└── site/              # Built static site (git-ignored)
```

## 🛠️ Active Projects

### [ffiec-data-connect](https://github.com/call-report/ffiec-data-connect)
Modern Python wrapper for FFIEC Webservice APIs with OAuth2 support and multiple output formats.

### [data-collector](https://github.com/call-report/data-collector)
Universal bulk data collector for FFIEC/US Bank Regulatory data with CLI interface.

## 📝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This work is licensed under [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).

## 📧 Contact

- **Issues**: [GitHub Issues](https://github.com/call-report/ffiec-data-connect/issues)
- **Email**: m@mikeh.dev
- **Website**: [call.report](https://call.report)

## 🔄 Recent Updates

- **September 2025**: Documentation modernization and content refresh
- **August 2025**: Updated data-collector to v2.0
- **Active Development**: ffiec-data-connect with REST API support

---

*Last Updated: September 8, 2025*
# Build Verification

Verification was run after committing the port branches and before creating this case-study index.

## Commands

For each ported project:

```powershell
git diff --check origin/1.21.4..HEAD
.\gradlew.bat build -PfabricOnly
```

## Results

| Project | Whitespace check | Fabric-only build |
| --- | --- | --- |
| YUNG's API | Passed | Passed |
| YUNG's Better End Island | Passed | Passed |
| YUNG's Better Strongholds | Passed | Passed |
| YUNG's Bridges | Passed | Passed |

## Notes

- Builds emitted existing Javadoc/deprecation warnings that did not fail the build.
- YUNG's API and Bridges emitted non-fatal remap warnings during Fabric remapping.
- The dependency mods built against the local sibling `../yungapi` port where configured.

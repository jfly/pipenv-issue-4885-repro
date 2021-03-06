A simple repro of https://github.com/pypa/pipenv/issues/4885.

To run the repro, you'll need at least two terminals open.

In terminal 1:

    $ docker compose up

In terminal 2:

    ## See how few hashes show up here? ##

    $ docker compose run pipenv-broken
    root@ba3778621867:/app# pipenv --version
    pipenv, version 2021.11.23
    root@ba3778621867:/app# pipenv lock
    ...
    root@ba3778621867:/app# cat Pipfile.lock | jq ".default.greenlet"
    {
      "hashes": [
        "sha256:e30f5ea4ae2346e62cedde8794a56858a67b878dd79f7df76a0767e356b1744a",
        "sha256:eb6ea6da4c787111adf40f697b4e58732ee0942b5d3bd8f435277643329ba627",
        "sha256:ec8c433b3ab0419100bd45b47c9c8551248a5aee30ca5e9d399a0b57ac04651b",
        "sha256:f3acda1924472472ddd60c29e5b9db0cec629fbe3c5c5accb74d6d6d14773478"
      ],
      "index": "jfly local",
      "version": "==1.1.2"
    }

    ## See all the hashes that show up here? ##

    $ docker compose run pipenv-working
    root@37e6ff3c283e:/app# pipenv --version
    pipenv, version 2020.11.15
    root@37e6ff3c283e:/app# pipenv lock
    ...
    root@37e6ff3c283e:/app# cat Pipfile.lock | jq ".default.greenlet"
    {
      "hashes": [
        "sha256:0051c6f1f27cb756ffc0ffbac7d2cd48cb0362ac1736871399a739b2885134d3",
        "sha256:00e44c8afdbe5467e4f7b5851be223be68adb4272f44696ee71fe46b7036a711",
        "sha256:013d61294b6cd8fe3242932c1c5e36e5d1db2c8afb58606c5a67efce62c1f5fd",
        "sha256:049fe7579230e44daef03a259faa24511d10ebfa44f69411d99e6a184fe68073",
        "sha256:14d4f3cd4e8b524ae9b8aa567858beed70c392fdec26dbdb0a8a418392e71708",
        "sha256:166eac03e48784a6a6e0e5f041cfebb1ab400b394db188c48b3a84737f505b67",
        "sha256:17ff94e7a83aa8671a25bf5b59326ec26da379ace2ebc4411d690d80a7fbcf23",
        "sha256:1e12bdc622676ce47ae9abbf455c189e442afdde8818d9da983085df6312e7a1",
        "sha256:21915eb821a6b3d9d8eefdaf57d6c345b970ad722f856cd71739493ce003ad08",
        "sha256:288c6a76705dc54fba69fbcb59904ae4ad768b4c768839b8ca5fdadec6dd8cfd",
        "sha256:2bde6792f313f4e918caabc46532aa64aa27a0db05d75b20edfc5c6f46479de2",
        "sha256:32ca72bbc673adbcfecb935bb3fb1b74e663d10a4b241aaa2f5a75fe1d1f90aa",
        "sha256:356b3576ad078c89a6107caa9c50cc14e98e3a6c4874a37c3e0273e4baf33de8",
        "sha256:40b951f601af999a8bf2ce8c71e8aaa4e8c6f78ff8afae7b808aae2dc50d4c40",
        "sha256:572e1787d1460da79590bf44304abbc0a2da944ea64ec549188fa84d89bba7ab",
        "sha256:58df5c2a0e293bf665a51f8a100d3e9956febfbf1d9aaf8c0677cf70218910c6",
        "sha256:64e6175c2e53195278d7388c454e0b30997573f3f4bd63697f88d855f7a6a1fc",
        "sha256:7227b47e73dedaa513cdebb98469705ef0d66eb5a1250144468e9c3097d6b59b",
        "sha256:7418b6bfc7fe3331541b84bb2141c9baf1ec7132a7ecd9f375912eca810e714e",
        "sha256:7cbd7574ce8e138bda9df4efc6bf2ab8572c9aff640d8ecfece1b006b68da963",
        "sha256:7ff61ff178250f9bb3cd89752df0f1dd0e27316a8bd1465351652b1b4a4cdfd3",
        "sha256:833e1551925ed51e6b44c800e71e77dacd7e49181fdc9ac9a0bf3714d515785d",
        "sha256:8639cadfda96737427330a094476d4c7a56ac03de7265622fcf4cfe57c8ae18d",
        "sha256:8c5d5b35f789a030ebb95bff352f1d27a93d81069f2adb3182d99882e095cefe",
        "sha256:8c790abda465726cfb8bb08bd4ca9a5d0a7bd77c7ac1ca1b839ad823b948ea28",
        "sha256:8d2f1fb53a421b410751887eb4ff21386d119ef9cde3797bf5e7ed49fb51a3b3",
        "sha256:903bbd302a2378f984aef528f76d4c9b1748f318fe1294961c072bdc7f2ffa3e",
        "sha256:93f81b134a165cc17123626ab8da2e30c0455441d4ab5576eed73a64c025b25c",
        "sha256:95e69877983ea39b7303570fa6760f81a3eec23d0e3ab2021b7144b94d06202d",
        "sha256:9633b3034d3d901f0a46b7939f8c4d64427dfba6bbc5a36b1a67364cf148a1b0",
        "sha256:97e5306482182170ade15c4b0d8386ded995a07d7cc2ca8f27958d34d6736497",
        "sha256:9f3cba480d3deb69f6ee2c1825060177a22c7826431458c697df88e6aeb3caee",
        "sha256:aa5b467f15e78b82257319aebc78dd2915e4c1436c3c0d1ad6f53e47ba6e2713",
        "sha256:abb7a75ed8b968f3061327c433a0fbd17b729947b400747c334a9c29a9af6c58",
        "sha256:aec52725173bd3a7b56fe91bc56eccb26fbdff1386ef123abb63c84c5b43b63a",
        "sha256:b11548073a2213d950c3f671aa88e6f83cda6e2fb97a8b6317b1b5b33d850e06",
        "sha256:b1692f7d6bc45e3200844be0dba153612103db241691088626a33ff1f24a0d88",
        "sha256:b336501a05e13b616ef81ce329c0e09ac5ed8c732d9ba7e3e983fcc1a9e86965",
        "sha256:b8c008de9d0daba7b6666aa5bbfdc23dcd78cafc33997c9b7741ff6353bafb7f",
        "sha256:b92e29e58bef6d9cfd340c72b04d74c4b4e9f70c9fa7c78b674d1fec18896dc4",
        "sha256:be5f425ff1f5f4b3c1e33ad64ab994eed12fc284a6ea71c5243fd564502ecbe5",
        "sha256:dd0b1e9e891f69e7675ba5c92e28b90eaa045f6ab134ffe70b52e948aa175b3c",
        "sha256:e30f5ea4ae2346e62cedde8794a56858a67b878dd79f7df76a0767e356b1744a",
        "sha256:e6a36bb9474218c7a5b27ae476035497a6990e21d04c279884eb10d9b290f1b1",
        "sha256:e859fcb4cbe93504ea18008d1df98dee4f7766db66c435e4882ab35cf70cac43",
        "sha256:eb6ea6da4c787111adf40f697b4e58732ee0942b5d3bd8f435277643329ba627",
        "sha256:ec8c433b3ab0419100bd45b47c9c8551248a5aee30ca5e9d399a0b57ac04651b",
        "sha256:eff9d20417ff9dcb0d25e2defc2574d10b491bf2e693b4e491914738b7908168",
        "sha256:f0214eb2a23b85528310dad848ad2ac58e735612929c8072f6093f3585fd342d",
        "sha256:f276df9830dba7a333544bd41070e8175762a7ac20350786b322b714b0e654f5",
        "sha256:f3acda1924472472ddd60c29e5b9db0cec629fbe3c5c5accb74d6d6d14773478",
        "sha256:f70a9e237bb792c7cc7e44c531fd48f5897961701cdaa06cf22fc14965c496cf",
        "sha256:f9d29ca8a77117315101425ec7ec2a47a22ccf59f5593378fc4077ac5b754fce",
        "sha256:fa877ca7f6b48054f847b61d6fa7bed5cebb663ebc55e018fda12db09dcc664c",
        "sha256:fdcec0b8399108577ec290f55551d926d9a1fa6cad45882093a7a07ac5ec147b"
      ],
      "index": "jfly local",
      "version": "==1.1.2"
    }

# ObjectiveHarmonyPatch

[Harmony](https://github.com/pardeike/Harmony) のパッチをオブジェクティブに管理できるようにします。

## Usage

### パッチの作成

```C#
MethodBase myMethod = /* 関連付けたいメソッドの MethodBase */;
HarmonyPatch patch = HarmonyPatch.Patch("MyPatch", myMethod, PatchType.Prefix);
patch.Invoked += Prefix;

PatchInvokationResult Prefix(object sender, PatchInvokedEventArgs e)
{
    // 実行したい処理

    return new PatchInvokationResult(/* 戻り値 */, SkipModes.SkipOriginal);
    // または
    // return PatchInvokationResult.DoNothing(e);
};
```

### パッチの解放

```C#
patch.Dispose();
```

## インストール方法

[NuGet](https://www.nuget.org/packages/ObjectiveHarmonyPatch) からパッケージをインストールしてください。

## 使用ライブラリ等

#### [Harmony](https://github.com/pardeike/Harmony) (MIT)

Copyright (c) 2017  Andreas Pardeike
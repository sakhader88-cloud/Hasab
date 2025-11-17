class WorkAtDay {
  WorkAtDay({required this.start, required this.end, required this.selected});
  DateTime start = DateTime.now();
  DateTime end = DateTime.now();
  bool selected = false;
}

import 'package:flutter/services.dart';
import 'package:path_provider/path_provider.dart';
import 'dart:io';

class FileReader {
  static Future<String> getLocalPath() async {
    var dir = await getApplicationCacheDirectory();
    return dir.path;
  }

  static Future<File> getLocalFile(String fileName) async {
    String path = await getLocalPath();
    return File('$path/$fileName.txt');
  }

  static Future<File> writeFile(
    String fileName,
    String str,
  ) async {
    File file = await getLocalFile(fileName);

    return file.writeAsString(str);
  }

  static Future<File> appendFile(
    String fileName,
    String str,
  ) async {
    File file = await getLocalFile(fileName);

    return file.writeAsString(str, mode: FileMode.append);
  }

  static Future<String> readFile(String fileName) async {
    try {
      final file = await getLocalFile(fileName);
      String content = await file.readAsString();
      return content;
    } catch (e) {
      return "";
    }
  }
}
// This is a basic Flutter widget test.
//
// To perform an interaction with a widget in your test, use the WidgetTester
// utility in the flutter_test package. For example, you can send tap and scroll
// gestures. You can also use WidgetTester to find child widgets in the widget
// tree, read text, and verify that the values of widget properties are correct.

import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

import 'package:flutter_application_1/main.dart';

void main() {
  testWidgets('Counter increments smoke test', (WidgetTester tester) async {
    // Build our app and trigger a frame.
    await tester.pumpWidget(const MyApp());

    // Verify that our counter starts at 0.
    expect(find.text('0'), findsOneWidget);
    expect(find.text('1'), findsNothing);

    // Tap the '+' icon and trigger a frame.
    await tester.tap(find.byIcon(Icons.add));
    await tester.pump();

    // Verify that our counter has incremented.
    expect(find.text('0'), findsNothing);
    expect(find.text('1'), findsOneWidget);
  });
}
pluginManagement {
    def flutterSdkPath = {
        def properties = new Properties()
        file("local.properties").withInputStream { properties.load(it) }
        def flutterSdkPath = properties.getProperty("flutter.sdk")
        assert flutterSdkPath != null, "flutter.sdk not set in local.properties"
        return flutterSdkPath
    }
    settings.ext.flutterSdkPath = flutterSdkPath()

    includeBuild("${settings.ext.flutterSdkPath}/packages/flutter_tools/gradle")

    plugins {
        id "dev.flutter.flutter-gradle-plugin" version "1.0.0" apply false
    }
}

include ":app"

apply from: "${settings.ext.flutterSdkPath}
org.gradle.jvmargs=-Xmx1536M
android.useAndroidX=true
android.enableJetifier=true
pluginManagement {
    def flutterSdkPath = {
        def properties = new Properties()
        file("local.properties").withInputStream { properties.load(it) }
        def flutterSdkPath = properties.getProperty("flutter.sdk")
        assert flutterSdkPath != null, "flutter.sdk not set in local.properties"
        return flutterSdkPath
    }
    settings.ext.flutterSdkPath = flutterSdkPath()

    includeBuild("${settings.ext.flutterSdkPath}/packages/flutter_tools/gradle")

    plugins {
        id "dev.flutter.flutter-gradle-plugin" version "1.0.0" apply false
    }
}

include ":app"

apply from: "${settings.ext.flutterSdkPath}/packages/

import 'dart:async';

import 'package:flutter/material.dart';
import 'package:sigi_owlytics/ui/screens/base/widgets/base_state_without_bloc.dart';
import 'package:sigi_owlytics/ui/screens/report_nature_of_injury/body_widget/models/person_model.dart';
import 'package:sigi_owlytics/ui/screens/report_nature_of_injury/flow_widgets/nature_of_injury/nature_of_injury_types.dart';

class PersonWidget extends StatefulWidget {
  final bool _isBackSidePerson;
  final StreamSink<MapEntry<dynamic, String>> _sink;
  final List<String> _selectedBodyParts;

  const PersonWidget(
    this._isBackSidePerson,
    this._sink,
    this._selectedBodyParts, {
    Key key,
  }) : super(key: key);

  @override
  _PersonWidgetState createState() => _PersonWidgetState();
}

class _PersonWidgetState extends BaseStateWithoutBloc<PersonWidget> {
  final PersonModel _personBack = PersonModel(true);
  final PersonModel _personFront = PersonModel(false);

  bool get _isBack => widget._isBackSidePerson;

  List<String> get selectedBodyParts => widget._selectedBodyParts;

  StreamSink<MapEntry<dynamic, String>> get _sink => widget._sink;


  @override
  void initState() {
    super.initState();
    initBodies();
  }

  @override
  Widget getWidget(BuildContext context) {
    return Container(
      width: screenUtil.setWidth(204),
      height: screenUtil.setHeight(435),
      child: Stack(
        children: <Widget>[
          getHead(),
          getNeck(),
          getBody(),
          getBottom(),
          getLArm(),
          getLElbow(),
          getLForearm(),
          getLHand(),
          getRArm(),
          getRElbow(),
          getRForearm(),
          getRHand(),
          getLThigh(),
          getLKnee(),
          getLLeg(),
          getLFoot(),
          getRThigh(),
          getRKnee(),
          getRLeg(),
          getRFoot(),
        ],
      ),
    );
  }

  Widget getHead() => Positioned(
        left: screenUtil.setWidth(79),
        width: screenUtil.setWidth(41),
        height: screenUtil.setHeight(_isBack ? 45 : 47),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.headModel.backHeadResource : _personFront.headModel.frontHeadResource));
              setState(() => _isBack
                  ? _personBack.headModel.isHeadSelected = !_personBack.headModel.isHeadSelected
                  : _personFront.headModel.isHeadSelected = !_personFront.headModel.isHeadSelected);
            },
            child: _isBack
                ? _personBack.headModel.isHeadSelected
                    ? _personBack.headModel.backHead.value
                    : _personBack.headModel.backHead.key
                : _personFront.headModel.isHeadSelected
                    ? _personFront.headModel.frontHead.value
                    : _personFront.headModel.frontHead.key),
      );

  Widget getNeck() => Positioned(
        left: screenUtil.setWidth(85),
        top: screenUtil.setHeight(_isBack ? 45 : 46),
        width: screenUtil.setWidth(29),
        height: screenUtil.setHeight(_isBack ? 13 : 12),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.headModel.backNeckResource : _personFront.headModel.frontNeckResource));
              setState(() => _isBack
                  ? _personBack.headModel.isNeckSelected = !_personBack.headModel.isNeckSelected
                  : _personFront.headModel.isNeckSelected = !_personFront.headModel.isNeckSelected);
            },
            child: _isBack
                ? _personBack.headModel.isNeckSelected
                    ? _personBack.headModel.backNeck.value
                    : _personBack.headModel.backNeck.key
                : _personFront.headModel.isNeckSelected
                    ? _personFront.headModel.frontNeck.value
                    : _personFront.headModel.frontNeck.key),
      );

  Widget getBody() => Positioned(
        left: screenUtil.setWidth(60),
        top: screenUtil.setHeight(59),
        width: screenUtil.setWidth(80),
        height: screenUtil.setHeight(_isBack ? 128 : 136),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.bodyModel.bBodyResource : _personFront.bodyModel.fBodyResource));
              setState(() => _isBack
                  ? _personBack.bodyModel.isBodySelected = !_personBack.bodyModel.isBodySelected
                  : _personFront.bodyModel.isBodySelected = !_personFront.bodyModel.isBodySelected);
            },
            child: _isBack
                ? _personBack.bodyModel.isBodySelected
                    ? _personBack.bodyModel.backBody.value
                    : _personBack.bodyModel.backBody.key
                : _personFront.bodyModel.isBodySelected
                    ? _personFront.bodyModel.frontBody.value
                    : _personFront.bodyModel.frontBody.key),
      );

  Widget getBottom() => Positioned(
        left: screenUtil.setWidth(53),
        bottom: screenUtil.setHeight(213),
        width: screenUtil.setWidth(93),
        height: screenUtil.setHeight(_isBack ? 36 : 33),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.bodyModel.bBottomResource : _personFront.bodyModel.fBottomResource));
              setState(() => _isBack
                  ? _personBack.bodyModel.isBottomSelected = !_personBack.bodyModel.isBottomSelected
                  : _personFront.bodyModel.isBottomSelected = !_personFront.bodyModel.isBottomSelected);
            },
            child: _isBack
                ? _personBack.bodyModel.isBottomSelected
                    ? _personBack.bodyModel.backBottom.value
                    : _personBack.bodyModel.backBottom.key
                : _personFront.bodyModel.isBottomSelected
                    ? _personFront.bodyModel.frontBottom.value
                    : _personFront.bodyModel.frontBottom.key),
      );

  Widget getLArm() => Positioned(
        left: screenUtil.setWidth(35),
        top: screenUtil.setHeight(70),
        width: screenUtil.setWidth(26),
        height: screenUtil.setHeight(54),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lArmModel.bArmResource : _personFront.lArmModel.fArmResource));
              setState(() => _isBack
                  ? _personBack.lArmModel.isArmSelected = !_personBack.lArmModel.isArmSelected
                  : _personFront.lArmModel.isArmSelected = !_personFront.lArmModel.isArmSelected);
            },
            child: _isBack
                ? _personBack.lArmModel.isArmSelected
                    ? _personBack.lArmModel.bArm.value
                    : _personBack.lArmModel.bArm.key
                : _personFront.lArmModel.isArmSelected
                    ? _personFront.lArmModel.fArm.value
                    : _personFront.lArmModel.fArm.key),
      );

  Widget getLElbow() => Positioned(
        left: screenUtil.setWidth(25),
        top: screenUtil.setHeight(98),
        width: screenUtil.setWidth(30),
        height: screenUtil.setHeight(70),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lArmModel.bElbowResource : _personFront.lArmModel.fElbowResource));
              setState(() => _isBack
                  ? _personBack.lArmModel.isElbowSelected = !_personBack.lArmModel.isElbowSelected
                  : _personFront.lArmModel.isElbowSelected = !_personFront.lArmModel.isElbowSelected);
            },
            child: _isBack
                ? _personBack.lArmModel.isElbowSelected
                    ? _personBack.lArmModel.bElbow.value
                    : _personBack.lArmModel.bElbow.key
                : _personFront.lArmModel.isElbowSelected
                    ? _personFront.lArmModel.fElbow.value
                    : _personFront.lArmModel.fElbow.key),
      );

  Widget getLForearm() => Positioned(
        left: screenUtil.setWidth(8),
        top: screenUtil.setHeight(142),
        width: screenUtil.setWidth(42),
        height: screenUtil.setHeight(48),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lArmModel.bForearmResource : _personFront.lArmModel.fForearmResource));
              setState(() => _isBack
                  ? _personBack.lArmModel.isForearmSelected = !_personBack.lArmModel.isForearmSelected
                  : _personFront.lArmModel.isForearmSelected = !_personFront.lArmModel.isForearmSelected);
            },
            child: _isBack
                ? _personBack.lArmModel.isForearmSelected
                    ? _personBack.lArmModel.bForearm.value
                    : _personBack.lArmModel.bForearm.key
                : _personFront.lArmModel.isForearmSelected
                    ? _personFront.lArmModel.fForearm.value
                    : _personFront.lArmModel.fForearm.key),
      );

  Widget getLHand() => Positioned(
        left: screenUtil.setWidth(2),
        top: screenUtil.setHeight(192),
        width: screenUtil.setWidth(22),
        height: screenUtil.setHeight(22),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lArmModel.bHandResource : _personFront.lArmModel.fHandResource));
              setState(() => _isBack
                  ? _personBack.lArmModel.isHandSelected = !_personBack.lArmModel.isHandSelected
                  : _personFront.lArmModel.isHandSelected = !_personFront.lArmModel.isHandSelected);
            },
            child: _isBack
                ? _personBack.lArmModel.isHandSelected
                    ? _personBack.lArmModel.bHand.value
                    : _personBack.lArmModel.bHand.key
                : _personFront.lArmModel.isHandSelected
                    ? _personFront.lArmModel.fHand.value
                    : _personFront.lArmModel.fHand.key),
      );

  Widget getRArm() => Positioned(
        right: screenUtil.setWidth(39),
        top: screenUtil.setHeight(69),
        width: screenUtil.setWidth(26),
        height: screenUtil.setHeight(54),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rArmModel.bArmResource : _personFront.rArmModel.fArmResource));
              setState(() => _isBack
                  ? _personBack.rArmModel.isArmSelected = !_personBack.rArmModel.isArmSelected
                  : _personFront.rArmModel.isArmSelected = !_personFront.rArmModel.isArmSelected);
            },
            child: _isBack
                ? _personBack.rArmModel.isArmSelected
                    ? _personBack.rArmModel.bArm.value
                    : _personBack.rArmModel.bArm.key
                : _personFront.rArmModel.isArmSelected
                    ? _personFront.rArmModel.fArm.value
                    : _personFront.rArmModel.fArm.key),
      );

  Widget getRElbow() => Positioned(
        right: screenUtil.setWidth(29),
        top: screenUtil.setHeight(98),
        width: screenUtil.setWidth(30),
        height: screenUtil.setHeight(70),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rArmModel.bElbowResource : _personFront.rArmModel.fElbowResource));
              setState(() => _isBack
                  ? _personBack.rArmModel.isElbowSelected = !_personBack.rArmModel.isElbowSelected
                  : _personFront.rArmModel.isElbowSelected = !_personFront.rArmModel.isElbowSelected);
            },
            child: _isBack
                ? _personBack.rArmModel.isElbowSelected
                    ? _personBack.rArmModel.bElbow.value
                    : _personBack.rArmModel.bElbow.key
                : _personFront.rArmModel.isElbowSelected
                    ? _personFront.rArmModel.fElbow.value
                    : _personFront.rArmModel.fElbow.key),
      );

  Widget getRForearm() => Positioned(
        right: screenUtil.setWidth(10),
        top: screenUtil.setHeight(143),
        width: screenUtil.setWidth(42),
        height: screenUtil.setHeight(48),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rArmModel.bForearmResource : _personFront.rArmModel.fForearmResource));
              setState(() => _isBack
                  ? _personBack.rArmModel.isForearmSelected = !_personBack.rArmModel.isForearmSelected
                  : _personFront.rArmModel.isForearmSelected = !_personFront.rArmModel.isForearmSelected);
            },
            child: _isBack
                ? _personBack.rArmModel.isForearmSelected
                    ? _personBack.rArmModel.bForearm.value
                    : _personBack.rArmModel.bForearm.key
                : _personFront.rArmModel.isForearmSelected
                    ? _personFront.rArmModel.fForearm.value
                    : _personFront.rArmModel.fForearm.key),
      );

  Widget getRHand() => Positioned(
        right: screenUtil.setWidth(4),
        top: screenUtil.setHeight(192),
        width: screenUtil.setWidth(22),
        height: screenUtil.setHeight(22),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rArmModel.bHandResource : _personFront.rArmModel.fHandResource));
              setState(() => _isBack
                  ? _personBack.rArmModel.isHandSelected = !_personBack.rArmModel.isHandSelected
                  : _personFront.rArmModel.isHandSelected = !_personFront.rArmModel.isHandSelected);
            },
            child: _isBack
                ? _personBack.rArmModel.isHandSelected
                    ? _personBack.rArmModel.bHand.value
                    : _personBack.rArmModel.bHand.key
                : _personFront.rArmModel.isHandSelected
                    ? _personFront.rArmModel.fHand.value
                    : _personFront.rArmModel.fHand.key),
      );

  Widget getLThigh() => Positioned(
        left: screenUtil.setWidth(52),
        top: screenUtil.setHeight(224),
        width: screenUtil.setWidth(47),
        height: screenUtil.setHeight(72),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lLegModel.bThighResource : _personFront.lLegModel.fThighResource));
              setState(() => _isBack
                  ? _personBack.lLegModel.isThighSelected = !_personBack.lLegModel.isThighSelected
                  : _personFront.lLegModel.isThighSelected = !_personFront.lLegModel.isThighSelected);
            },
            child: _isBack
                ? _personBack.lLegModel.isThighSelected
                    ? _personBack.lLegModel.bThigh.value
                    : _personBack.lLegModel.bThigh.key
                : _personFront.lLegModel.isThighSelected
                    ? _personFront.lLegModel.fThigh.value
                    : _personFront.lLegModel.fThigh.key),
      );

  Widget getLKnee() => Positioned(
        left: screenUtil.setWidth(51),
        top: screenUtil.setHeight(298),
        width: screenUtil.setWidth(33),
        height: screenUtil.setHeight(_isBack ? 26 : 29),
        child: Container(
          child: GestureDetector(
              onTap: () {
                _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                    _isBack ? _personBack.lLegModel.bKneeResource : _personFront.lLegModel.fKneeResource));
                setState(() => _isBack
                    ? _personBack.lLegModel.isKneeSelected = !_personBack.lLegModel.isKneeSelected
                    : _personFront.lLegModel.isKneeSelected = !_personFront.lLegModel.isKneeSelected);
              },
              child: _isBack
                  ? _personBack.lLegModel.isKneeSelected
                      ? _personBack.lLegModel.bKnee.value
                      : _personBack.lLegModel.bKnee.key
                  : _personFront.lLegModel.isKneeSelected
                      ? _personFront.lLegModel.fKnee.value
                      : _personFront.lLegModel.fKnee.key),
        ),
      );

  Widget getLLeg() => Positioned(
        left: screenUtil.setWidth(48),
        top: screenUtil.setHeight(325),
        width: screenUtil.setWidth(30),
        height: screenUtil.setHeight(81),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lLegModel.bLegResource : _personFront.lLegModel.fLegResource));
              setState(() => _isBack
                  ? _personBack.lLegModel.isLegSelected = !_personBack.lLegModel.isLegSelected
                  : _personFront.lLegModel.isLegSelected = !_personFront.lLegModel.isLegSelected);
            },
            child: _isBack
                ? _personBack.lLegModel.isLegSelected
                    ? _personBack.lLegModel.bLeg.value
                    : _personBack.lLegModel.bLeg.key
                : _personFront.lLegModel.isLegSelected
                    ? _personFront.lLegModel.fLeg.value
                    : _personFront.lLegModel.fLeg.key),
      );

  Widget getLFoot() => Positioned(
        left: screenUtil.setWidth(40),
        top: screenUtil.setHeight(407),
        width: screenUtil.setWidth(26),
        height: screenUtil.setHeight(22),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.lLegModel.bFootResource : _personFront.lLegModel.fFootResource));
              setState(() => _isBack
                  ? _personBack.lLegModel.isFootSelected = !_personBack.lLegModel.isFootSelected
                  : _personFront.lLegModel.isFootSelected = !_personFront.lLegModel.isFootSelected);
            },
            child: _isBack
                ? _personBack.lLegModel.isFootSelected
                    ? _personBack.lLegModel.bFoot.value
                    : _personBack.lLegModel.bFoot.key
                : _personFront.lLegModel.isFootSelected
                    ? _personFront.lLegModel.fFoot.value
                    : _personFront.lLegModel.fFoot.key),
      );

  Widget getRThigh() => Positioned(
        right: screenUtil.setWidth(58),
        top: screenUtil.setHeight(224),
        width: screenUtil.setWidth(47),
        height: screenUtil.setHeight(72),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rLegModel.bThighResource : _personFront.rLegModel.fThighResource));
              setState(() => _isBack
                  ? _personBack.rLegModel.isThighSelected = !_personBack.rLegModel.isThighSelected
                  : _personFront.rLegModel.isThighSelected = !_personFront.rLegModel.isThighSelected);
            },
            child: _isBack
                ? _personBack.rLegModel.isThighSelected
                    ? _personBack.rLegModel.bThigh.value
                    : _personBack.rLegModel.bThigh.key
                : _personFront.rLegModel.isThighSelected
                    ? _personFront.rLegModel.fThigh.value
                    : _personFront.rLegModel.fThigh.key),
      );

  Widget getRKnee() => Positioned(
        right: screenUtil.setWidth(57),
        top: screenUtil.setHeight(297),
        width: screenUtil.setWidth(33),
        height: screenUtil.setHeight(_isBack ? 26 : 29),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rLegModel.bKneeResource : _personFront.rLegModel.fKneeResource));
              setState(() => _isBack
                  ? _personBack.rLegModel.isKneeSelected = !_personBack.rLegModel.isKneeSelected
                  : _personFront.rLegModel.isKneeSelected = !_personFront.rLegModel.isKneeSelected);
            },
            child: _isBack
                ? _personBack.rLegModel.isKneeSelected
                    ? _personBack.rLegModel.bKnee.value
                    : _personBack.rLegModel.bKnee.key
                : _personFront.rLegModel.isKneeSelected
                    ? _personFront.rLegModel.fKnee.value
                    : _personFront.rLegModel.fKnee.key),
      );

  Widget getRLeg() => Positioned(
        right: screenUtil.setWidth(55),
        top: screenUtil.setHeight(325),
        width: screenUtil.setWidth(30),
        height: screenUtil.setHeight(81),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rLegModel.bLegResource : _personFront.rLegModel.fLegResource));
              setState(() => _isBack
                  ? _personBack.rLegModel.isLegSelected = !_personBack.rLegModel.isLegSelected
                  : _personFront.rLegModel.isLegSelected = !_personFront.rLegModel.isLegSelected);
            },
            child: _isBack
                ? _personBack.rLegModel.isLegSelected
                    ? _personBack.rLegModel.bLeg.value
                    : _personBack.rLegModel.bLeg.key
                : _personFront.rLegModel.isLegSelected
                    ? _personFront.rLegModel.fLeg.value
                    : _personFront.rLegModel.fLeg.key),
      );

  Widget getRFoot() => Positioned(
        right: screenUtil.setWidth(48),
        top: screenUtil.setHeight(407),
        width: screenUtil.setWidth(26),
        height: screenUtil.setHeight(22),
        child: GestureDetector(
            onTap: () {
              _sink.add(MapEntry(NatureOfInjuryType.PERSON,
                  _isBack ? _personBack.rLegModel.bFootResource : _personFront.rLegModel.fFootResource));
              setState(() => _isBack
                  ? _personBack.rLegModel.isFootSelected = !_personBack.rLegModel.isFootSelected
                  : _personFront.rLegModel.isFootSelected = !_personFront.rLegModel.isFootSelected);
            },
            child: _isBack
                ? _personBack.rLegModel.isFootSelected
                    ? _personBack.rLegModel.bFoot.value
                    : _personBack.rLegModel.bFoot.key
                : _personFront.rLegModel.isFootSelected
                    ? _personFront.rLegModel.fFoot.value
                    : _personFront.rLegModel.fFoot.key),
      );

  void initBodies() {
    if (selectedBodyParts != null && selectedBodyParts.isNotEmpty) {
      _personBack.checkSelectedBodyParts(selectedBodyParts);
      _personFront.checkSelectedBodyParts(selectedBodyParts);
    }
  }
}

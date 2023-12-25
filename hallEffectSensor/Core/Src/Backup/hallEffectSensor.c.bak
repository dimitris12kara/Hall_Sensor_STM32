/*
 * hallEffectSensor.c
 *
 *  Created on: Dec 25, 2023
 *      Author: Karamanlis Dimitris
 */
#include "hallEffectSensor.h"

// Initializes the hallEffectSensor Structure
HAL_StatusTypeDef hallEffectInit(hallEffectSensor *_hf, float _radius, TIM_HandleTypeDef _counter, TIM_HandleTypeDef _timeOutTimer, float _tuner, uint16_t _interruptPin){
	_hf->isReady = 0;
	_hf->radius = _radius;
	_hf->counter = &_counter;
	_hf->timeOutTimer = &_timeOutTimer;
	_hf->tuner = _tuner;
	_hf->clock_ratio = HAL_RCC_GetHCLKFreq()/(_hf->counter->Init.Prescaler+1);
	_hf->interruptPin = _interruptPin;
	return HAL_TIM_Base_Start_IT(_hf->timeOutTimer);
}

void hallEffectCalculator(hallEffectSensor *_hf){
	  if(_hf->isReady==1){
		  _hf->isReady=0;
		  _hf->time_now = __HAL_TIM_GET_COUNTER(_hf->counter);
		  _hf->rpm = PI*_hf->clock_ratio/(_hf->time_now-_hf->time_before);
		  _hf->vehicle_speed = 2*PI*_hf->radius*_hf->rpm;
		  _hf->rpm = GEAR_RATIO*(RPM_CONVERSION*_hf->rpm)*_hf->tuner;
		  _hf->time_before = _hf->time_now;
		  _hf->timeOutTimer->Instance->CNT = 0;
	  }
	  return;
}


